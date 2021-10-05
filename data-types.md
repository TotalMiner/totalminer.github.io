# (Unofficial) XML Modding API Documentation

## Pages
- [Index](/index)
- [Data Types](/data-types)
- [Adding and Modifying Items](/items)
- [Modifying Blocks](/blocks)
- [Adding and Modifying NPCs](/npcs)

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

 An object as { [float](#float) X, [float](#float) Y }.

## Vector3

 An object as { [float](#float) X, [float](#float) Y, [float](#float) Z }.

## Item

 A Total Miner item ID. No spaces are allowed. Can usually be either an existing item or a custom item. In some rare situations, custom item IDs do not work here.

## Block

 A Total Miner block ID. No spaces are allowed. Must be an existing block.

## InventoryItemXML

 An object as { [Item](#item) Item, [ushort](#ushort) Durability, [int](#int) Count }.

## InventoryItemNDXML

 An object as { [Item](#item) Item, [int](#int) Count }.