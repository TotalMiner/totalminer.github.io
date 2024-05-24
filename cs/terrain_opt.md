
# (Official) C# Modding Documentation

## Pages

- [Home](../index)
- [Terrain Generation Setup](terrain)
- [Terrain Generation Option 1](terrain1)
- [Terrain Generation Option 2](terrain2)

##### **Note:** This guide is a work in progress (WIP) and the Terrain Generation Modding API as described in this guide has not yet been released to public versions of the game.
___

# Terrain Generation Optimization

This guide is based on the code in the [Terrain Generation Option 2 Guide](terrain2). You might want to do that guide first, although the concepts presented here are equally valid for Option 1 terrain generation.

Fast terrain generation is vitally important for immersion in Total Miner. With this in mind it is important we make efforts to ensure our terrain generation is as efficient and optimal as possible.

It might help to run the game and your mod at this time and observe how fast your generation executes. 

## Chunk Flags

To start with, there are two very easy optimizations we can do immediately.

The game has two ChunkFlags that help it avoid doing costly lighting and mesh updates where they are not necessary.

They are: 
- `ChunkFlags.ChunkIsAllAir`
- `ChunkFlags.ChunkIsAllSolid`

If we know we are not writing any voxels to the chunk, we can flag it as `ChunkIsAllAir` and then the game knows it does not have to update it's lighting or its mesh.
Similarly if we know that every voxel in the chunk is a solid voxel we can flag it as `ChunkIsAllSolid` and the game knows it does not have to update its lighting, and in some cases (such as all neighbours are also AllSolid) then it does not need to update it's mesh.

Setting just these two flags correctly after generation can often enable dramatically faster terrain generation.

## Terrain Generation Option 2

We will continue the optimization guide based on this [Terrain Generation Option 2](terrain2) guide.

At the top of the `GenerateChunk()` method where we Fill the chunk with Basalt, the Fill call is passing `ChunkFlags.None` as the 2nd parameter. If we change that to `ChunkIsAllSolid` then the game will know it does not have to update lighting or meshes for the solid `Basalt` chunks underground.

Change:
```cs
chunk.Fill(new MapBlock() { BlockID = (byte)Block.Basalt }, ChunkFlags.None);
```
to
```cs
chunk.Fill(new MapBlock() { BlockID = (byte)Block.Basalt }, ChunkFlags.ChunkIsAllSolid);
```

Build and run your mod. You should immediately notice a dramatic increase in terrain generation speed.

All chunks above height 224 can be flagged as `IsAllAir` because we do not generate any voxels for them.

At the bottom of the `GenerateChunk()` method insert:
```cs
chunk.SetChunkFlag(ChunkFlags.ChunkIsAllAir);
```

We also need to ensure there is a `return` statement directly after the `((MapChunk)chunk).DownNeighbour().SetChunkFlag(ChunkFlags.LightDirty)` call so that we don't set `IsAllAir` for chunks that actually have voxels.

The full method should look like this:
```cs
public void GenerateChunk(ITMMapChunk chunk)
{
    // just fill in the whole chunk with Basalt if it is below the map height of 224
    if (chunk.GlobalOffset.Y < 224)
    {
        chunk.Fill(new MapBlock() { BlockID = (byte)Block.Basalt }, ChunkFlags.ChunkIsAllSolid);
        return;
    }
            
    if (chunk.GlobalOffset.Y == 224)
    {
        if (random == null)
            // random is null the first time this generator object is used
            random = new PcgRandom((ulong)map.Seed, (ulong)chunk.GlobalOffset.GetHashCode());
        else
            // if random was instantiated before, it was for a different chunk, so reseed it to this chunks seed
            random.Seed((ulong)map.Seed, (ulong)chunk.GlobalOffset.GetHashCode());

        // only populate wood into half of the chunks
        if (random.Next(2) == 0)
        {
            if (blockCache == null)
                // create the voxel cache if not yet created
                blockCache = new byte[map.ChunkLength];
            else
                // reset the cache if already created
                Array.Clear(blockCache);

            // populate somewhere between 10 and 30 wood 'tables' for each chunk
            int count = random.Next(10, 30);
            for (int i = 0; i < count; ++i)
            {
                // pick a random x, z position within the chunk
                int x = random.Next(map.ChunkSize.X);
                int z = random.Next(map.ChunkSize.Z);

                // don't generate if near chunk edge
                if (x > 2 && x < map.ChunkSize.X - 3 && z > 2 && z < map.ChunkSize.Z - 3)
                {
                    // the mushroom 'trunk'
                    blockCache[GetChunkIndex(x, 0, z)] = (byte)Block.Wood; // y=0 is the bottom plane of the chunk
                    for (int xx = x - 2; xx < x + 3; ++xx)
                    {
                        // the mushroom 'roof'
                        for (int zz = z - 2; zz < z + 3; ++zz)
                        {
                            blockCache[GetChunkIndex(xx, 1, zz)] = (byte)Block.Wood;
                            ushort h = (ushort)(1 + chunk.GlobalOffset.Y);
                            chunk.Region.HeightMap.SetHeight(xx + chunk.GlobalOffset.X, zz + chunk.GlobalOffset.Z, h, h);
                        }
                    }
                }
            }

            // the voxel data is now written so we must commit it back to a
            // compressed RLEStream which is the underlying voxel storage
            // we must cast ITMChunk to MapChunk to compress to the RLEStream
            ((MapChunk)chunk).BlockData.CompressNoLockNoCCM(blockCache);

            // we have written voxel data into this chunk, so flag it as needing a lighting update
            chunk.SetChunkFlag(ChunkFlags.LightDirty);

            // the voxels we have written will require the chunk below to also have its lighting updated
            ((MapChunk)chunk).DownNeighbour().SetChunkFlag(ChunkFlags.LightDirty);
            return;
        }
    }
    chunk.SetChunkFlag(ChunkFlags.ChunkIsAllAir);
}
```

Again build and run your mod and you should notice even faster generation.


## More Optimization

Now it starts to become harder to optimize, and we must use general C# optimization techniques. I will present a few techniques here which are relatively easy to do.

The main thing to remember is even the smallest improvement can make a big difference because the `GenerateChunk()` and `DecorateChunk()` methods are called many thousands of times for each world. Eg. If you can improve your chunk Generation speed by just 1 millisecond, that will allow the game to generate a 1024 x 1024 world faster by up to 16 seconds.

The first thing we need to know to optimize is how fast the current code executes. For this we need a `StopWatch` object.

All optimization should be done using Release builds to ensure more accurate performance timings.

Add a StopWatch declaration under your `blockCache` declaration and a static maxTicks field:
```cs
Stopwatch stopwatch = new Stopwatch();
public static long MaxTicks;
```

Immediately after we have determined we are definitely going to generate some tree mushrooms we should restart the timer.
```cs
stopwatch.Restart();
```

Then immediately after we have finished generating the mushrooms we should take a reading of the timer.
```cs
long ticks = stopwatch.ElapsedTicks;
if (ticks > MaxTicks) MaxTicks = ticks;
```
We don't want to stop the timer because that may incur some overhead and affect our timings. So we just take a reading then compare it to our maxTicks and if it's more, we store it in maxTicks.

We also want to take the reading before we compress the voxel data or set chunk flags because those operations cannot be avoided and we can't control the efficiency of them anyway.

So at the end of a full world generation `TerrainGuideTerrainGen.maxTicks` will equal the maximum ticks spent by a single chunk generation.

We need some way to see MaxTicks, so we will draw it to the screen every frame. Add an `ITMGame game` member variable to your `class TerraTutPlugin : ITMPlugin` and initialize it in the `Initialize()` method:
```cs
ITMGame game;

public void InitializeGame(ITMGame game)
{
    this.game = game;
    TerrainGuideTerrainGen.MaxTicks = 0;
}
```

We also reset MaxTicks here so it restarts for each world gen.

And draw it in the `Draw()` method to the top left of the screen like so:
```cs
public void Draw(ITMPlayer player, ITMPlayer virtualPlayer, Viewport vp)
{
    game.SpriteBatch.Begin();
    game.SpriteBatch.DrawString(Globals1.FontConsolas10, $"ticks:{TerrainGuideTerrainGen.MaxTicks}", Vector2.One, Color.Yellow);
    game.SpriteBatch.End();
}
```
During optimization timings it's preferable if the code is performing a similar # of operations per timing, so for this exercise we will generate a consistent # of mushrooms. We will take the medium of 10 and 30 = 20.

Change the `count` assignment to:
```cs
int count = 20;// random.Next(10, 30);
```

Full method:

```cs
if (random.Next(2) == 0)
{
    stopwatch.Restart();
                 
    if (blockCache == null)
        // create the voxel cache if not yet created
        blockCache = new byte[map.ChunkLength];
    else
        // reset the cache if already created
        Array.Clear(blockCache);

    // populate somewhere between 10 and 30 wood 'tables' for each chunk
    int count = random.Next(10, 30);
    for (int i = 0; i < count; ++i)
    {
        // pick a random x, z position within the chunk
        int x = random.Next(map.ChunkSize.X);
        int z = random.Next(map.ChunkSize.Z);

        // don't generate if near chunk edge
        if (x > 2 && x < map.ChunkSize.X - 3 && z > 2 && z < map.ChunkSize.Z - 3)
        {
            // the mushroom 'trunk'
            blockCache[GetChunkIndex(x, 0, z)] = (byte)Block.Wood; // y=0 is the bottom plane of the chunk
            for (int xx = x - 2; xx < x + 3; ++xx)
            {
                // the mushroom 'roof'
                for (int zz = z - 2; zz < z + 3; ++zz)
                {
                    blockCache[GetChunkIndex(xx, 1, zz)] = (byte)Block.Wood;
                    ushort h = (ushort)(1 + chunk.GlobalOffset.Y);
                    chunk.Region.HeightMap.SetHeight(xx + chunk.GlobalOffset.X, zz + chunk.GlobalOffset.Z, h, h);
                }
            }
        }
    }

    long ticks = stopwatch.ElapsedTicks;
    if (ticks > maxTicks) maxTicks = ticks;

    // the voxel data is now written so we must commit it back to a
    // compressed RLEStream which is the underlying voxel storage
    // we must cast ITMChunk to MapChunk to compress to the RLEStream
    ((MapChunk)chunk).BlockData.CompressNoLockNoCCM(blockCache);

    // we have written voxel data into this chunk, so flag it as needing a lighting update
    chunk.SetChunkFlag(ChunkFlags.LightDirty);

    // the voxels we have written will require the chunk below to also have its lighting updated
    ((MapChunk)chunk).DownNeighbour().SetChunkFlag(ChunkFlags.LightDirty);
    return;
}
```

Now that we can run the game/mod multiple times, take max timing of the `GenerateChunk()` method and view it on the screen, we can now make some optimization changes and see if the ticks decrease.

## Properties

Property getters usually involve a method call, which is slower than a direct read from a field. All values obtained via `ITM` interfaces are via property getters. For values we will be using a lot, and thereby invoking many property getter calls, we can cache the value to a field and use the field instead.

In our generation the following getters can be cached:
- `map.ChunkSize`
- `chunk.GlobalOffset`

Add the caches:
```cs
Point3D chunkSize;
GlobalPoint3D chunkGlobalOffset;
```

And assign them before first use:
- Assign `chunkGlobalOffset` at the very top of `GenerateChunk()` and replace all uses of `chunk.GlobalOffset` with `chunkGlobalOffset`
- Assign `chunkSize` just above the assignment to `int count` and replace all use of `map.ChunkSize` with `chunkSize`, including in the `GetChunkIndex()` method.

Build and run your mod and see if ticks has reduced.

## Get Out of the Loop

Another optimization technique I will present here is pulling local variable declarations outside of tight loops. Often the compiler will do this for us but it doesn't always, so it's a good habit to use if you need faster code.

We use loops to generate the wood mushroom, so we can pull all variable declarations in those loops out and declare them above the loops.

```cs
for (int i = 0; i < count; ++i)
{
    // pick a random x, z position within the chunk
    int x = random.Next(chunkSize.X);
    int z = random.Next(chunkSize.Z);

    // don't generate if near chunk edge
    if (x > 2 && x < chunkSize.X - 3 && z > 2 && z < chunkSize.Z - 3)
    {
        // the mushroom 'trunk'
        blockCache[GetChunkIndex(x, 0, z)] = (byte)Block.Wood; // y=0 is the bottom plane of the chunk
        for (int xx = x - 2; xx < x + 3; ++xx)
        {
            // the mushroom 'roof'
            for (int zz = z - 2; zz < z + 3; ++zz)
            {
                blockCache[GetChunkIndex(xx, 1, zz)] = (byte)Block.Wood;
                ushort h = (ushort)(1 + chunkGlobalOffset.Y);
                chunk.Region.HeightMap.SetHeight(xx + chunkGlobalOffset.X, zz + chunkGlobalOffset.Z, h, h);
            }
        }
    }
}
```
Becomes:
```cs
ushort h;
int x, z, xx, zz;
int count = 20;// random.Next(10, 30);
for (int i = 0; i < count; ++i)
{
    // pick a random x, z position within the chunk
    x = random.Next(chunkSize.X);
    z = random.Next(chunkSize.Z);

    // don't generate if near chunk edge
    if (x > 2 && x < chunkSize.X - 3 && z > 2 && z < chunkSize.Z - 3)
    {
        // the mushroom 'trunk'
        blockCache[GetChunkIndex(x, 0, z)] = (byte)Block.Wood; // y=0 is the bottom plane of the chunk
        for (xx = x - 2; xx < x + 3; ++xx)
        {
            // the mushroom 'roof'
            for (zz = z - 2; zz < z + 3; ++zz)
            {
                blockCache[GetChunkIndex(xx, 1, zz)] = (byte)Block.Wood;
                h = (ushort)(1 + chunkGlobalOffset.Y);
                chunk.Region.HeightMap.SetHeight(xx + chunkGlobalOffset.X, zz + chunkGlobalOffset.Z, h, h);
            }
        }
    }
}
```

## Help I'm Desperate

If you are absolutely desperate to shave off a few more cycles, you can make some last ditch changes. These changes will depend on the very specific nature of your code and your data and won't always be applicable.

Our `GenerateChunk()` method is performing several addition and subtraction operations with constant data that never changes. We can save cycles by caching the results of those operations.

We can cache `chunkSize.X - 3` and `chunkSize.Z - 3`
We can cache `x + 3`, `z - 2` and `z - 3`, and `h`
We can cache `xx + chunkGlobalOffset.X`

```cs
ushort h = (ushort)(1 + chunkGlobalOffset.Y);
int x, z, xx, zz;
int chunkSizeX_m3 = chunkSize.X - 3;
int chunkSizeZ_m3 = chunkSize.Z - 3;
int chunkGlobalOffsetX_xx;
int x_a3, z_m2, z_a3;
int count = 20;// random.Next(10, 30);
for (int i = 0; i < count; ++i)
{
    // pick a random x, z position within the chunk
    x = random.Next(chunkSize.X);
    z = random.Next(chunkSize.Z);

    // don't generate if near chunk edge
    if (x > 2 && x < chunkSizeX_m3 && z > 2 && z < chunkSizeZ_m3)
    {
        // the mushroom 'trunk'
        blockCache[GetChunkIndex(x, 0, z)] = (byte)Block.Wood; // y=0 is the bottom plane of the chunk

        x_a3 = x + 3;
        z_m2 = z - 2;
        z_a3 = z + 3;
        for (xx = x - 2; xx < x_a3; ++xx)
        {
            chunkGlobalOffsetX_xx = xx + chunkGlobalOffset.X;
            // the mushroom 'roof'
            for (zz = z_m2; zz < z_a3; ++zz)
            {
                blockCache[GetChunkIndex(xx, 1, zz)] = (byte)Block.Wood;
                chunk.Region.HeightMap.SetHeight(chunkGlobalOffsetX_xx, zz + chunkGlobalOffset.Z, h, h);
            }
        }
    }
}
```

## I'm More Desperate than a 16 year old Male Nerd

Okay Okay. Unwind / Inline `GetChunkIndex()`

## Full code:
```cs
using StudioForge.BlockWorld;
using StudioForge.Engine.Core;
using StudioForge.TotalMiner;
using StudioForge.TotalMiner.API;
using System;
using System.Diagnostics;

namespace TerrainGuide2
{
    class TerrainGuideTerrainGen : ITMTerrainGenerator
    {
        ITMMap map;
        PcgRandom random;
        byte[] blockCache;
        Stopwatch stopwatch = new Stopwatch();
        public static long MaxTicks;
        Point3D chunkSize;
        GlobalPoint3D chunkGlobalOffset;

        public ITMMap Map => map;
        public ITMTerrainPreview TerrainPreviewer => throw new System.NotImplementedException();

        #region Initialization

        public void Initialize(ITMWorld world, ITMMap map, BiomeParams biomeParams)
        {
            this.map = map;
        }

        public void InitializeForChunk(GlobalPoint3D chunkGlobalOffset, ulong seed)
        {
            throw new System.NotImplementedException();
        }

        public void InitializeForGeneralUse(ITMMapChunk newChunk)
        {
        }

        public void InitializeForGeneralUse(GlobalPoint3D p)
        {
        }

        public void InitializeForPreview(BiomeParams biomeParams, BoxInt mapBound, ushort seaLevel, int seed)
        {
            throw new System.NotImplementedException();
        }

        public void PreGenerateCaves()
        {
        }

        #endregion

        #region Generation

        public void GenerateChunk(ITMMapChunk chunk)
        {
            chunkGlobalOffset = chunk.GlobalOffset;

            // just fill in the whole chunk with Basalt if it is below the map height of 224
            if (chunkGlobalOffset.Y < 224)
            {
                chunk.Fill(new MapBlock() { BlockID = (byte)Block.Basalt }, ChunkFlags.ChunkIsAllSolid);
                return;
            }
            
            if (chunkGlobalOffset.Y == 224)
            {
                if (random == null)
                    // random is null the first time this generator object is used
                    random = new PcgRandom((ulong)map.Seed, (ulong)chunkGlobalOffset.GetHashCode());
                else
                    // if random was instantiated before, it was for a different chunk, so reseed it to this chunks seed
                    random.Seed((ulong)map.Seed, (ulong)chunkGlobalOffset.GetHashCode());

                // only populate wood into half of the chunks
                if (random.Next(2) == 0)
                {
                    stopwatch.Restart();
                 
                    if (blockCache == null)
                        // create the voxel cache if not yet created
                        blockCache = new byte[map.ChunkLength];
                    else
                        // reset the cache if already created
                        Array.Clear(blockCache);

                    chunkSize = map.ChunkSize;
                    int j, x, z, xx, zz;
                    int chunkSizeX_m3 = chunkSize.X - 3;
                    int chunkSizeZ_m3 = chunkSize.Z - 3;
                    int chunkPlane = chunkSize.X * chunkSize.Z;
                    int chunkGlobalOffsetX_xx;
                    int x_a3, z_m2, z_a3;
                    ushort h = (ushort)(1 + chunkGlobalOffset.Y);

                    // populate somewhere between 10 and 30 wood 'tables' for each chunk
                    int count = 20;// random.Next(10, 30);
                    for (int i = 0; i < count; ++i)
                    {
                        // pick a random x, z position within the chunk
                        x = random.Next(chunkSize.X);
                        z = random.Next(chunkSize.Z);

                        // don't generate if near chunk edge
                        if (x > 2 && x < chunkSizeX_m3 && z > 2 && z < chunkSizeZ_m3)
                        {
                            // the mushroom 'trunk'
                            blockCache[x + (z * chunkSize.X)] = (byte)Block.Wood; // y=0 is the bottom plane of the chunk

                            x_a3 = x + 3;
                            z_m2 = z - 2;
                            z_a3 = z + 3;
                            for (xx = x - 2; xx < x_a3; ++xx)
                            {
                                chunkGlobalOffsetX_xx = xx + chunkGlobalOffset.X;
                                j = xx + z_m2 * chunkSize.X + chunkPlane;
                                // the mushroom 'roof'
                                for (zz = z_m2; zz < z_a3; ++zz)
                                {
                                    blockCache[j] = (byte)Block.Wood;
                                    j += chunkSize.X;
                                    chunk.Region.HeightMap.SetHeight(chunkGlobalOffsetX_xx, zz + chunkGlobalOffset.Z, h, h);
                                }
                            }
                        }
                    }

                    long ticks = stopwatch.ElapsedTicks;
                    if (ticks > MaxTicks) MaxTicks = ticks;

                    // the voxel data is now written so we must commit it back to a
                    // compressed RLEStream which is the underlying voxel storage
                    // we must cast ITMChunk to MapChunk to compress to the RLEStream
                    ((MapChunk)chunk).BlockData.CompressNoLockNoCCM(blockCache);

                    // we have written voxel data into this chunk, so flag it as needing a lighting update
                    chunk.SetChunkFlag(ChunkFlags.LightDirty);

                    // the voxels we have written will require the chunk below to also have its lighting updated
                    ((MapChunk)chunk).DownNeighbour().SetChunkFlag(ChunkFlags.LightDirty);
                    return;
                }
            }

            chunk.SetChunkFlag(ChunkFlags.ChunkIsAllAir);
        }

        #endregion

        #region Decoration

        public void DecorateChunk(ITMMapChunk chunk)
        {
        }

        #endregion

        #region Implementation

        //int GetChunkIndex(int x, int y, int z) => x + (z * chunkSize.X) + (y * chunkSize.X * chunkSize.Z);

        public int GetGroundHeight(int globalX, int globalZ) => 224;

        #endregion
    }
}
```
___

Happy optimizing!

- [Home](../index)
