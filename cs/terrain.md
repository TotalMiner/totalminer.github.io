
# (Official) C# Modding Documentation

## Pages

- [Home](../index)

#### **Note:** This guide is a work in progress (WIP) and the Terrain Generation Modding API as described in this guide has not yet been released to public versions of the game.
___

# Terrain Generation

This guide assumes you already have a mod setup and working with the game.

See this [linked guide](https://github.com/DaveTheMonitor/TMModTutorial/blob/master/README.md) if you do not.

## Overview

There are two main options for modding Total Miner Terrain Generation:
- Subclassing a base generation helper (easier)
- Complete override (harder)

The first option is easier because a base implementation is provided for you and you override parts of it to change the generation. The provided implementation is almost the same as the implementation used by the game itself for the built in terrain. We would recommend using this option until you are more familiar with the games generation.

The second option is harder and gives you complete control of the terrain generation but you must implement everything yourself. Only use this option if you are familiar with how the game generates terrain.

This guide shows how to setup your mod for both options, and then it will direct you to other guides for the options you want to use.

## Getting Started

The first thing you must do is add a plugin for Terrain Generation. This plugin implements `ITMPluginTerrain`.

Add a new class file called `TerrainPlugin.cs` and insert the following code:
```cs
using StudioForge.Engine.Core;
using StudioForge.TotalMiner;
using StudioForge.TotalMiner.API;

namespace ModName
{
    internal class TerrainPlugin : ITMPluginTerrain
    {
        public static Pool<TerrainGenerator> Pool = new Pool<TerrainGenerator>();

        public ITMTerrainGenerator AllocateTerrainGen(ushort terrainID, out int handle)
        {
            handle = Pool.GetNext();
            return Pool.List[handle];
        }

        public bool ReleaseTerrainGen(ushort terrainID, int handle)
        {
            Pool.Release(handle);
            return true;
        }
    }
}
```
This is just boilerplate code that allocates terrain generators from a pool. They are allocated from a pool because they are used by multiple threads and used thousands of times per world generation so instantiating a new instance each time would create a lot of garbage and potential performance issues.

This Pool is using the `TerrainGenerator` class provided by the game which gives support for basic terrain generation scaffolding. Later on you will change this to your own `ITMPluginTerrain` implementation which may be either a sub class of `TerrainGenerator` or an entirely new implementation of `ITMTerrainGenerator`.

Now change your `ITMPluginProvider` to return an instance of your `TerrainPlugin`:

Change:
```cs
public ITMPluginBiome GetPluginBiome() => null
```
to 
```cs
public ITMPluginTerrain GetPluginTerrain() => new TerrainPlugin();
```

## Setting Up Some Base Parameters

Now you must add the following method to your `ITMPlugin` implementation. If you used the linked guide above to setup your mod, the implementation class is likely called `{ModName}PluginProvider`

```cs
        public void InitializeStart(ModHeaderData data)
        {
            data.BiomeType = BiomeType.Modded;
            data.MaxHeight = 50;
            data.MaxSeaDepth = 10;
        }
```

This is just setting up some basic parameters for terrain generation.
- `BiomeType.Modded` is telling the game that your mod wants to generate the terrain.
- `MaxHeight` is the maximum number of blocks above sea level that land will generate.
- `MaxSeaDepth` is the maximum depth (below sea level) of any body of water.

## Ready To Go

And that's it. That's all the code necessary to start modding Total Miner terrain.
- Compile your mod and run the game.
- Select a new world.
- It doesn't matter what terrain/biome type you choose as your mod will be overriding it.
- Activate your mod.

Now when you load into the world, it should look something like this:

![VanillaTerrain](../Images/vanilla_terrain.png)

This is vanilla terrain generating automatically for you using the `TerrainGenerator` base class provided by the game.

You are now ready to modify the games built in terrain generation.

Create a new class file `ModNameTerrainGen.cs` and insert the following code:

```cs
using StudioForge.TotalMiner;

namespace ModName
{
    public class ModNameTerrainGen : TerrainGenerator
    {
    }
}
```

Now change the Pool type in TerrainPlugin.cs from `TerrainGenerator`:

```cs
public static Pool<TerrainGenerator> Pool = new Pool<TerrainGenerator>();
```
to `ModNameTerrainGen`
```cs
public static Pool<ModNameTerrainGen> Pool = new Pool<ModNameTerrainGen>();
```

This is telling the Pool allocator to now allocate instances of your terrain generator instead of the games helper generator.

# Next Step

Now choose the appropriate guide for the terrain modding you want to do:

- [Option 1 (Easier):](terrain1) Sub class the provided `TerrainGenerator` helper to give you basic terrain generation and scaffolding to modify it.

- [Option 2 (Harder):](terrain2) Implement `ITMTerrainGenerator` to write your own terrain generator from scratch.

- [Home](../index)