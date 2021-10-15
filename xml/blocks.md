# (Unofficial) XML Modding API Documentation

## Pages
- [Home](../index)
- [XML Documentation](xml-doc)
- [Data Types](data-types)
- [Adding and Modifying Items](items)
- [Modifying Blocks](blocks)
- [Adding and Modifying NPCs](npcs)
- [Adding Particle Templates](particles)

# Modifying Blocks

At the moment, blocks cannot be added with mods, but they can be modified. Below is the documentation for each file used to modify blocks. Any file or field can be omitted.

To modify the name, description, price, etc of blocks, you must use [ItemData.xml](items#itemdataxml) with the desired Block ID as the Item ID.
- [BlockData.xml](#blockdataxml)
- [BlockMaterialData.xml](#blockmaterialdataxml)
- [BlockTextures16.xml/BlockTextures64.xml](#blocktextures16xmlblocktextures64xml)

---

## BlockData.xml:

Contains general information about this block.

### BlockID: [Block](data-types#block)

The ID of this block. This must be an existing block ID.

### Material: [BlockMaterial](#blockmaterialdataxml)

The material of this block. The material affects this block's resistance and tool efficiencies. Must be an existing block material.
- Valid Values: Clay, Sondstone, Limestone, Basalt, Andesite, Dacite, Diorite, Tuff, Serpentine, Gabbro, Granite, Komatiite, Marble, Rhyolite, Bedrock, Flint, Copper, Cassiterite, Coal, Iron, Gold, Opal, Carbon, Sulphur, Cyclonite, Fluorite, Platinum, Greenstone, Diamond, Sapphire, Ruby, Titanium, Obsidian, Uranium, Composite, SoftComposite, Glass, FramedGlass, Stick, Wood, Leaves, Earth, Sand, Porous, Snow, Crop, Vegetation, Vapor, Liquid, Fire, Ice, Paper, Brick, Stone, Metal, Explosive, Key, Fibre, Color, SpiderEgg, Barrier

### ClassType: [DataBlockType](#blockclassdataxml)

Additional block type data for blocks with special functions. Must be an existing class type. Most blocks use None.
- Valid Values: None, ParticleEmitter, Door, Marker, Shop, Chest, Furnace, Bookcase, AmbientSound, SentryTurret, ProximityDetector, Fire, NPCSpawn, Script, Sign, MobSpawn, Teleport, WifiReceiver, WifiTransmitter, Crop, Blueprint, WisdomScroll, Sundial, Torch, Painting, Book, Health

### Opacity: [byte](data-types#byte)

How opaque this block is. Affects how much light passes through this block.
- Valid Values: 1-15 for transparent blocks, 255 for opaque blocks.

### Luminance: [byte](data-types#byte)

How much light this block emits.
- Valid Values: 0-15

### Friction: [float](data-types#float)

The friction of this block. The lower the friction, the more "slippery" this block is. Most blocks use 0.35.
- Valid Values: 0-1

### Dampen: [float](data-types#float)

Unknown

### Buffer: [byte](data-types#byte)

The way this block is rendered when placed in the world.
- Valid Values: 0 = Full Block, 1 = Special, 2 = 2D, 3 = Transparent

### IsIcon: [bool](data-types#bool)

If true, this block's texture is an icon. Should be used with Buffer 2 and low opacity.

### IsAttached: [bool](data-types#bool)

If true, this block should be attached to another block when placed. Can be used with Buffer 2.

### IsPassable: [bool](data-types#bool)

If true, this block will have no collision and can be walked through.

### IsRotated: [bool](data-types#bool)

If true, this block can be rotated.

### IsOrientated: [bool](data-types#bool)

If true, this block can be orientated.

### IsOreDeposit: [bool](data-types#bool)

If true, this block should be considered ore.

### IsPowerEmitter: [bool](data-types#bool)

If true, this block can emit power when active.

### IsPoweredMechanism: [bool](data-types#bool)

If true, this block can be activated by power.

### IsVertSunlightUnhindered: [bool](data-types#bool)

If true, sunlight can pass through this block vertically without being blocked.

### BlastResistance: [ushort](data-types#ushort)

How reistant this block is to explosions.

### WindAffect: [byte](data-types#byte)

How much this block sways when there is wind.

### TextureID: [byte](data-types#byte)

The textures list this block can use.

#### [Table of Contents](#modifying-blocks)

---

## BlockMaterialData.xml:

Contains information about this block material. The block material affects the tools that can break the block. If any efficiency is set to 0, that respective tool cannot break the block.

### Material: BlockMaterial

The ID of this block material. No spaces are allowed. Must be an existing block material.
- Valid Values: Clay, Sondstone, Limestone, Basalt, Andesite, Dacite, Diorite, Tuff, Serpentine, Gabbro, Granite, Komatiite, Marble, Rhyolite, Bedrock, Flint, Copper, Cassiterite, Coal, Iron, Gold, Opal, Carbon, Sulphur, Cyclonite, Fluorite, Platinum, Greenstone, Diamond, Sapphire, Ruby, Titanium, Obsidian, Uranium, Composite, SoftComposite, Glass, FramedGlass, Stick, Wood, Leaves, Earth, Sand, Porous, Snow, Crop, Vegetation, Vapor, Liquid, Fire, Ice, Paper, Brick, Stone, Metal, Explosive, Key, Fibre, Color, SpiderEgg, Barrier

### Resistance: [ushort](data-types#ushort)

The resistance of this material. The number of hits required to break a block of this material is equal to Block Resistance / Item Power × Tool Effectiveness. Eg. Rhyolite has a resistance of 7200, and a Titanium Pickaxe has a power of 1200, meaning it will take 6 hits to destroy Rhyolite with a Titanium Pickaxe.

### BaseEfficiency: [ushort](data-types#ushort)

The base percent efficiency of items when breaking a block of this material. The power of all tools when breaking a block with this material is affected by this value. Eg. if BaseEfficiency is 50, all tools will take twice as many hits to break a block with this material.

### PickEfficiency: [ushort](data-types#ushort)

The percent efficiency of pickaxes when breaking a block of this material.

### ShovelEfficiency: [ushort](data-types#ushort)

The percent efficiency of shovels when breaking a block of this material.

### HatchetEfficiency: [ushort](data-types#ushort)

The percent efficiency of hatchets when breaking a block of this material.

### WeaponEfficiency: [ushort](data-types#ushort)

The percent efficiency of weapons when breaking a block of this material.

### XPAdjust: [float](data-types#float)

The multiplier for XP earned when this block is broken. If this is 0, the xp earned is 1x.

### Flags: BlockMaterialFlags

Unused.

#### [Table of Contents](#modifying-blocks)

---

## BlockTextures16.xml/BlockTextures64.xml:

Contains the order of items in their respective texture atlas image. HD Texture Packs use BlockTextures64.xml while SD Texture Packs use BlockTextures16.xml. The texture atlas image should have every item texture laid out next to one another. Recommended up to 32 blocks on one line in the texture atlas. Once the 32nd block is reached, move down a line.

### BlockID: [Block](data-types#block)

The ID of this block.

#### [Table of Contents](#modifying-blocks)