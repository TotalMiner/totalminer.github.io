
# (Official) C# Modding Documentation

## Pages

- [Home](../index)
- [Terrain Generation Setup](terrain)
- [Terrain Generation Option 1](terrain1)

##### **Note:** This guide is a work in progress (WIP) and the Terrain Generation Modding API as described in this guide has not yet been released to public versions of the game.
___

# Terrain Generation

This guide assumes you already have a working mod setup for terrain generation.

See this [linked guide](terrain) if you do not.

## Overview

This guide will show how to implement modded terrain generation by implementing `ITMTerrainGenerator` from scratch.

Open `ModNameTerrainGen.cs` that was created in the [Terrain Gen Setup Guide](terrain.md).

Change:
```cs
public class ModNameTerrainGen : TerrainGenerator
```
to
```cs
public class ModNameTerrainGen : ITMTerrainGenerator
```

Use Quick Action to implement the interface:

![ImplementInterface](../images/implement_interface1.png)

The code should now look like this:
```cs
class ModNameTerrainGen : ITMTerrainGenerator
{
    public ITMMap Map => throw new System.NotImplementedException();

    public ITMTerrainPreview TerrainPreviewer => throw new System.NotImplementedException();

    public void DecorateChunk(ITMMapChunk chunk)
    {
        throw new System.NotImplementedException();
    }

    public void GenerateChunk(ITMMapChunk chunk)
    {
        throw new System.NotImplementedException();
    }

    public int GetGroundHeight(int globalX, int globalZ)
    {
        throw new System.NotImplementedException();
    }

    public void Initialize(ITMWorld world, ITMMap map, BiomeParams biomeParams)
    {
        throw new System.NotImplementedException();
    }

    public void InitializeForChunk(GlobalPoint3D chunkGlobalOffset, ulong seed)
    {
        throw new System.NotImplementedException();
    }

    public void InitializeForGeneralUse(ITMMapChunk newChunk)
    {
        throw new System.NotImplementedException();
    }

    public void InitializeForGeneralUse(GlobalPoint3D p)
    {
        throw new System.NotImplementedException();
    }

    public void InitializeForPreview(BiomeParams biomeParams, BoxInt mapBound, ushort seaLevel, int seed)
    {
        throw new System.NotImplementedException();
    }

    public void PreGenerateCaves()
    {
        throw new System.NotImplementedException();
    }
}
```

Insert the private member reference

`ITMMap map;`

above 

`public ITMMap Map => throw new System.NotImplementedException();`

Replace:

`public ITMMap Map => throw new System.NotImplementedException();`

with:

`public ITMMap Map => map;`

Replace:

`throw new System.NotImplementedException();`

in

`Initialize()`

with

`this.map = map;`

Remove

`throw new System.NotImplementedException();`

from the following methods:

```cs
public void DecorateChunk(ITMMapChunk chunk)
public void GenerateChunk(ITMMapChunk chunk)
public void InitializeForGeneralUse(ITMMapChunk newChunk)
public void InitializeForGeneralUse(GlobalPoint3D p)
public void PreGenerateCaves()
```

Replace

`throw new System.NotImplementedException();`

in

`GetGroundHeight()`

with

`return 0;`

The code should now look like this:
```cs
class ModNameTerrainGen : ITMTerrainGenerator
{
    ITMMap map;
    public ITMMap Map => map;

    public ITMTerrainPreview TerrainPreviewer => throw new System.NotImplementedException();

    public void DecorateChunk(ITMMapChunk chunk)
    {
    }

    public void GenerateChunk(ITMMapChunk chunk)
    {
    }

    public int GetGroundHeight(int globalX, int globalZ)
    {
        return 0;
    }

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
}
```

Build your Mod project. Fix any errors.

Copy the assembly (dll) file into the mod's deploy folder (under Saved Games).

Open the Terrain.xml file in the deploy folder and change it to:
```xml
<ModTerrainXML>
  <Name>TerrainFromScratch</Name>
</ModTerrainXML>
```

Run the game and activate your Mod. The `Terrain:` field on the Lobby tab should be `TerrainFromScratch`.

Start the world.

You should be standing at the bottom of an empty world.

![EmptyWorld](../images/empty_world.png)


## Code Reformat

At this point I'd suggest a slight reformat to the code to place methods in a more logical position within the class file, and to add some `#region` separation.

Change the `ModNameTerrainGen` class code so it now looks like this:
```cs
class ModNameTerrainGen : ITMTerrainGenerator
{
    ITMMap map;
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
    }

    #endregion

    #region Decoration

    public void DecorateChunk(ITMMapChunk chunk)
    {
    }

    #endregion

    #region Implementation

    public int GetGroundHeight(int globalX, int globalZ)
    {
        return 0;
    }

    #endregion
}
```

## Generation

Total Miner generates terrain by chunk. Each chunk contains 32 x 32 x 32 elements of voxel data. A 512 x 512 x 512 world would have 16 x 16 x 16 of these chunks. A 2048 x 512 x 2048 world would have 64 x 16 x 64 of these chunks.

The game determines the chunks that require generation at any given time and for each it calls the `void GenerateChunk(ITMMapChunk chunk)` method on the current `ITerrainGenerator` implementation. As a terrain generation modder, you write code in the `GenerateChunk()` method to put blocks (voxels) into each chunk as your terrain requires.

The `GenerateChunk()` method is passed an `ITMChunk` reference.

The `ITMChunk` interface does not give many options for writing voxel data. There are just 3 `Fill` methods which support filling regions of the chunk with voxel data.

For this guide we will use a fill method to completely fill chunks with Basalt that are positioned below height 225 (on the Y axis), effectively making the ground level a flat 224.

Add this code to the `GenerateChunk()` method.
```cs
public void GenerateChunk(ITMMapChunk chunk)
{
    if (chunk.GlobalOffset.Y < 224)
        chunk.Fill(new MapBlock() { BlockID = (byte)Block.Basalt }, ChunkFlags.None);
}
```

And change the `GetGroundHeight()` method to this:
```cs
public int GetGroundHeight(int globalX, int globalZ)
{
    return 224;
}
```

Build your mod and run the game. Activate your mod and you should see this when you start the world.

![BasaltWorld](../images/basalt_world.png)

## Writing Voxel Data

The `Fill` methods on the `ITMChunk` interface are good for writing blocks of voxels, but they are not efficient enough for writing thousands of voxels individually.

To write individual voxel data we must get access to the underlying block of RAM that stores the voxel data.

To do this we must cast the `ITMMap` reference to a `Map` reference.

`baseMap = map as Map`

All voxel data is stored in Run Length Encoded streams (RLEStream). This helps to dramatically reduce RAM requirements for large voxel worlds. But RLEStreams are not efficient or practical for writing voxel data. So the mechanism Total Miner uses is to acquire an unencoded thread safe cache or array of contiguous voxel data for writing, and once the writing is complete, we compress the cache back into an RLEStream and then release the cache for other parts of the game to use. Because the caches are acquired and released, the game is able to minimize system RAM allocations and avoid RAM fragmentation.

## The ChunkCacheManagers

The `Map` class has references to two ChunkCacheManagers which manage access to caches of memory used for uncompressed 8bit (byte) and 16bit (ushort) chunk voxel data.

We can call the appropriate ChunkCacheManager to acquire a thread safe cache or array of contiguous RAM to which we can then write uncompressed voxel data.
```cs
baseMap.ChunkByteCacheManager.AcquireCache(null, null, true, out blockCacheID, out blockCacheIndex);
byte[] blockCache = baseMap.ChunkByteCacheManager.Cache[blockCacheID];
```

The CacheManager manages several large blocks of contiguous RAM. When we acquire a cache, we don't get a reference to a sandboxed array just for that chunk, instead we get two indexes. The first index is to a large block of contiguous RAM, the block is much larger than the space of one chunk, so we also get the second index which is the start element in that block that we must access from. ie. We are using a sub block within a larger block. We must be careful not to write outside our range within the sub block.

So `blockCache` is a refence to a large array, and `blockCache[blockCacheIndex]` is the start element for our use.

Now we can write voxel data directly into that array (starting from index `blockCacheIndex`). After we have written the voxel data, we then compress it back to an RLEStream:
```cs
mapChunk.BlockData.SetStream(mapChunk, blockCacheID, blockCacheIndex);`
```

And finally release the cache back to the `ChunkCacheManager` for use by other parts of the game.
```cs
baseMap.ChunkByteCacheManager.DecRefCount(blockCacheID, blockCacheIndex);`
```

## GenerateChunkCore

Insert a new method under `GenerateChunk()`
```cs
bool GenerateChunkCore(ITMMapChunk chunk, byte[] blockCache, int blockCacheIndex)
{
}
```

We will use this method for the actual writing of voxel data, to keep it separate from the boilerplate code that acquires and releases caches, which will remain in the `GenerateChunk()` method.

We will now populate some random `Wood` blocks on the surface of the flat `Basalt` world. To do this we need a Random number generator.

Add the following to the top of the terrain generator class, under the `ITMMap map;` member declaration.

```cs
ITMMap map;
PcgRandom random; // add this
```

Now insert the following code into the end of the `GenerateChunk()` method.

```cs
    if (random == null)
        // random is null the first time this generator object is used
        random = new PcgRandom((ulong)map.Seed, (ulong)chunk.GlobalOffset.GetHashCode());
    else
        // if random was instantiated before, it was for a different chunk, so reseed it to this chunks seed
        random.Seed((ulong)map.Seed, (ulong)chunk.GlobalOffset.GetHashCode());

```

This instantiates the random generator if it has not yet been instantiated (it could have been instantiated if this terrain generator object has already been used for a previous chunk generation) and sets it's seed to the map seed + chunk hash.

If it has been previously instantiated then it just reseeds the existing object to the new chunk hash.

We can now use this `PcgRandom` object to generate random numbers.

Insert the following code into the `GenerateChunkCore()` method:

```cs
bool GenerateChunkCore(ITMMapChunk chunk, byte[] blockCache, int blockCacheIndex)
{
    // if we are the first chunk 'above' the basalt ground
    if (chunk.GlobalOffset.Y == 224)
    {
        // only populate wood into half of the chunks
        if (random.Next(2) == 0)
        {
            // populate somewhere between 10 and 49 (incl) wood blocks for each chunk
            int count = random.Next(10, 50);
            for (int i = 0; i < count; ++i)
            {
                // pick a random x, z position within the chunk
                int x = random.Next(map.ChunkSize.X);
                int z = random.Next(map.ChunkSize.Z);
                int j = GetChunkIndex(x, 0, z); // 0 is the bottom plane of the chunk
                blockCache[blockCacheIndex + j] = (byte)Block.Wood;
            }
            return true;
        }
    }
    return false;
}
```

This code checks the chunks Y position in the world, and if it is 224 then it is the chunk immediately above the top layer of Basalt, so we can populate the Wood blocks there.

It then calls `if (random.Next(2) == 0)` so that the following code is only executed for roughly every second chunk.

Next it gets a random number of Wood blocks to populate, any number from 10 to 49.

Then it loops for that count and calculates a random local X, Z position within the chunk for the block, then it calculates the index into the cache (array) and writes the Wood value.
It then returns true to signify the method call resulted in voxel data actually being written.

Otherwise it returns false if no voxel data was written. As you will see later, this allows for some optimization.

We have now written the code to write the random Wood voxels, but to use it, first we must write the code to acquire and release the cache.

Insert the following code under the `random` instantiation in the `GenerateChunk()` method:

```cs
    // we must cast to get access to the underlying voxel data
    var baseMap = map as Map; // we assume using StudioForge.BlockWorld.Map for your world
    short blockCacheID = -1;
    int blockCacheIndex = 0;

    try
    {
        // acquire an underlying voxel data cache for this chunk as an array of uncompressed voxel data
        baseMap.ChunkByteCacheManager.AcquireCache(null, null, true, out blockCacheID, out blockCacheIndex);
        // get a reference to the voxel data
        var blockCache = baseMap.ChunkByteCacheManager.Cache[blockCacheID];

        // write terrain generation code to fill the blockCache array with voxel data
        if (GenerateChunkCore(chunk, blockCache, blockCacheIndex))
        {
            // the voxel data is now written so we must commit it back to a compressed RLEStream which
            // is the underlying compressed voxel storage, and then we must release the uncompressed cache (for reuse by other code)
            // we must cast ITMChunk to MapChunk to set the RLEStream
            var mapChunk = chunk as MapChunk;
            mapChunk.BlockData.SetStream(mapChunk, blockCacheID, blockCacheIndex);
        }
    }
    finally
    {
        // release the acquired cache so the RAM can be reused by other parts of the game
        // this is in a finally block to ensure a thrown exception does not stop the uncompressed
        // cache from being released
        baseMap.ChunkByteCacheManager.DecRefCount(blockCacheID, blockCacheIndex);
    }
```

The entire method should now look like this:

```cs
public void GenerateChunk(ITMMapChunk chunk)
{
    // just fill in the whole chunk with Basalt if it is below the map height of 224
    if (chunk.GlobalOffset.Y < 224)
    {
        chunk.Fill(new MapBlock() { BlockID = (byte)Block.Basalt }, ChunkFlags.None);
        return;
    }

    if (random == null)
        // random is null the first time this generator object is used
        random = new PcgRandom((ulong)map.Seed, (ulong)chunk.GlobalOffset.GetHashCode());
    else
        // if random was instantiated before, it was for a different chunk, so reseed it to this chunks seed
        random.Seed((ulong)map.Seed, (ulong)chunk.GlobalOffset.GetHashCode());

    // we must cast to get access to the underlying voxel data
    var baseMap = map as Map; // we assume using StudioForge.BlockWorld.Map for your world
    short blockCacheID = -1;
    int blockCacheIndex = 0;

    try
    {
        // acquire an underlying voxel data cache for this chunk as an array of uncompressed voxel data
        baseMap.ChunkByteCacheManager.AcquireCache(null, null, true, out blockCacheID, out blockCacheIndex);
        // get a reference to the voxel data
        var blockCache = baseMap.ChunkByteCacheManager.Cache[blockCacheID];

        // write terrain generation code to fill the blockCache array with voxel data
        if (GenerateChunkCore(chunk, blockCache, blockCacheIndex))
        {
            // the voxel data is now written so we must commit it back to a compressed RLEStream which
            // is the underlying compressed voxel storage, and then we must release the uncompressed cache (for reuse by other code)
            // we must cast ITMChunk to MapChunk to set the RLEStream
            var mapChunk = chunk as MapChunk;
            mapChunk.BlockData.SetStream(mapChunk, blockCacheID, blockCacheIndex);
        }
    }
    finally
    {
        // release the acquired cache so the RAM can be reused by other parts of the game
        // this is in a finally block to ensure a thrown exception does not stop the uncompressed
        // cache from being released
        baseMap.ChunkByteCacheManager.DecRefCount(blockCacheID, blockCacheIndex);
    }
}
```

Add the following method into the #Implementation region, above or below the `GetGroundHeight()` method:

```cs
int GetChunkIndex(int x, int y, int z)
{
    return x + (z * map.ChunkSize.X) + (y * map.ChunkSize.X * map.ChunkSize.Z);
}
```

This helper method calculates the index into the chunks cache (array) of voxel data based on the local X,Y,Z coordinate of the voxel.

Now build your mod and run the game, and you should see something like this:

![WoodStumpWorld](../images/woodstumps_world.png)

If you are having build problems, here is the full code:

```cs
using StudioForge.BlockWorld;
using StudioForge.Engine.Core;
using StudioForge.TotalMiner;
using StudioForge.TotalMiner.API;
using System.Threading;

namespace TerrainGuide2
{
    class TerrainGuideTerrainGen : ITMTerrainGenerator
    {
        ITMMap map;
        PcgRandom random;

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
            // just fill in the whole chunk with Basalt if it is below the map height of 224
            if (chunk.GlobalOffset.Y < 224)
            {
                chunk.Fill(new MapBlock() { BlockID = (byte)Block.Basalt }, ChunkFlags.None);
                return;
            }

            if (random == null)
                // random is null the first time this generator object is used
                random = new PcgRandom((ulong)map.Seed, (ulong)chunk.GlobalOffset.GetHashCode());
            else
                // if random was instantiated before, it was for a different chunk, so reseed it to this chunks seed
                random.Seed((ulong)map.Seed, (ulong)chunk.GlobalOffset.GetHashCode());

            // the code below sets up thread safe voxel caches for writing. it doesn't actually do any terain generation.
            // it calls GenerateChunkCore(..) to do the actual terrain generation and voxel data writing

            // we must cast to get access to the underlying voxel data
            var baseMap = map as Map; // we assume using StudioForge.BlockWorld.Map for your world
            short blockCacheID = -1;
            int blockCacheIndex = 0;

            try
            {
                // acquire an underlying voxel data cache for this chunk as an array of uncompressed voxel data
                baseMap.ChunkByteCacheManager.AcquireCache(null, null, true, out blockCacheID, out blockCacheIndex);
                // get a reference to the voxel data
                var blockCache = baseMap.ChunkByteCacheManager.Cache[blockCacheID];

                // write terrain generation code to fill the blockCache array with voxel data
                if (GenerateChunkCore(chunk, blockCache, blockCacheIndex))
                {
                    // the voxel data is now written so we must commit it back to a compressed RLEStream which
                    // is the underlying compressed voxel storage, and then we must release the uncompressed cache (for reuse by other code)
                    // we must cast ITMChunk to MapChunk to set the RLEStream
                    var mapChunk = chunk as MapChunk;
                    mapChunk.BlockData.SetStream(mapChunk, blockCacheID, blockCacheIndex);
                }
            }
            finally
            {
                // release the acquired cache so the RAM can be reused by other parts of the game
                // this is in a finally block to ensure a thrown exception does not stop the uncompressed
                // cache from being released
                baseMap.ChunkByteCacheManager.DecRefCount(blockCacheID, blockCacheIndex);
            }
        }

        bool GenerateChunkCore(ITMMapChunk chunk, byte[] blockCache, int blockCacheIndex)
        {
            // this method does the actual terrain generation and writes the chunk voxel data

            // if we are the first chunk 'above' the basalt ground
            if (chunk.GlobalOffset.Y == 224)
            {
                // only populate wood into half of the chunks
                if (random.Next(2) == 0)
                {
                    // populate somewhere between 10 and 50 wood blocks for each chunk
                    int count = random.Next(10, 50);
                    for (int i = 0; i < count; ++i)
                    {
                        // pick a random x, z position within the chunk
                        int x = random.Next(map.ChunkSize.X);
                        int z = random.Next(map.ChunkSize.Z);
                        int j = GetChunkIndex(x, 0, z); // 0 is the bottom plane of the chunk
                        blockCache[blockCacheIndex + j] = (byte)Block.Wood;
                    }
                    return true;
                }
            }
            return false;
        }

        #endregion

        #region Decoration

        public void DecorateChunk(ITMMapChunk chunk)
        {
        }

        #endregion

        #region Implementation

        int GetChunkIndex(int x, int y, int z)
        {
            return x + (z * map.ChunkSize.X) + (y * map.ChunkSize.X * map.ChunkSize.Z);
        }

        public int GetGroundHeight(int globalX, int globalZ)
        {
            return 224;
        }

        #endregion
    }
}
```


The reason the `GenerateChunkCore()` method returns a bool to signify if it actually wrote voxel data is because if it didn't write any, then `GenerateChunk()` does not have to set the `RLEStream` for the chunk, and not setting the stream can save many CPU cycles, and with terrain generation we must save CPU cycles wherever possible to keep terrain generation fast.

This is the end of the guide for now. Good luck!

- [Home](../index)