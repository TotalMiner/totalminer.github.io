# (Unofficial) XML Modding API Documentation

## Pages
- [Home](../index)
- [XML Documentation](xml-doc)
- [Data Types](data-types)
- [Adding and Modifying Items](items)
- [Modifying Blocks](blocks)
- [Adding and Modifying NPCs](npcs)
- [Adding Particle Templates](particles)

# Data Types



## string

 A string of characters. Can be anything.

## bool

 True or False.

## int

 A whole number between -2,147,483,648 and 2,147,483,647.

## ushort

 A whole number between 0 and 65,535.

## short

 A whole number between -32,768 and 32,767.

## byte

 A whole number between 0 and 255.

## float

 A real number (decimal) between -3.4 x 10³⁸ and 3.4 x 10³⁸.

## Vector2

 An object representing two points.

#### [float](#float) X

#### [float](#float) Y

## Vector3

 An object representing three points.

#### [float](#float) X

#### [float](#float) Y

#### [float](#float) Z

## Vector4

 An object representing four points.

#### [float](#float) X

#### [float](#float) Y

#### [float](#float) Z

#### [float](#float) W

## Color

 An object representing an RGBA color.

#### [byte](#byte) R

#### [byte](#byte) G

#### [byte](#byte) B

#### [byte](#byte) A

## Item

 A Total Miner Item ID. No spaces are allowed. Can usually be either an existing item or a custom item. In some rare situations, custom item IDs do not work here.

## Block

 A Total Miner Block ID. No spaces are allowed. Must be an existing block.

## InventoryItemXML

 An object representing an item, amount, and durability.

#### [Item](#item) ItemID

#### [ushort](#ushort) Durability

#### [int](#int) Count

## InventoryItemNDXML

 An object representing an item and amount.

#### [Item](#item) ItemID

#### [int](#int) Count

## LootItem

 An object representing an item in a loot table.

#### [Item](#item) Item

The item of this loot drop.

#### DamageType Damage

The damage type required to make this item drop.
- Valid Values: Unknown, Combat, Drowning, Burning, ItemUse, Blast, BlockFallingOnHead, BlockCollision, Hail, ShieldDeflect, Effect

#### [int](#int) Percent

The percent chance of this item dropping.

#### [int](#int) Count1

The minimum amount of this item dropped.

#### [int](#int) Count2

The maximum amount of this item dropped.