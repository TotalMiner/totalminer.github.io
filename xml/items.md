# (Unofficial) XML Modding API Documentation

## Pages
- [Home](../index)
- [XML Documentation](xml-doc)
- [Data Types](data-types)
- [Adding and Modifying Items](items)
- [Modifying Blocks](blocks)
- [Adding and Modifying NPCs](npcs)
- [Adding Particle Templates](particles)

# Adding And Modifying Items

Items can be added and modified with XML mods. If an Item ID supplied already exists, that item will be modified. Below is the documentation for each file used to add and modify items. Any file or field can be omitted to use default values.
- [ItemData.xml](#itemdataxml)
- [ItemTypeData.xml](#itemtypedataxml)
- [ItemTypeClassData.xml](#itemtypeclassdataxml)
- [ItemCombatData.xml](#itemcombatdataxml)
- [ItemSwingTimeData.xml](#itemswingtimedataxml)
- [ItemSwingData.xml](#itemswingdataxml)
- [ItemSoundData.xml](#itemsounddataxml)
- [SkillData.xml](#skilldataxml)
- [BlueprintData.xml](#blueprintdataxml)
- [ItemTextures16.xml/ItemTextures32.xml](#itemtextures16xmlitemtextures32xml)

---

## ItemData.xml:

Contains general information about this item.

### ItemID: [Item](data-types#item)

The ID of this item. If this is an existing item, that item will be modified, otherwise this item will be added.

### Name: [string](data-types#string)

The name of this item that appears in the inventory, item interact screen, etc. The name can include spaces.

### Desc: [string](data-types#string)

The description of this item shown on this item interact screen.

### IsValid: [bool](data-types#bool)

If false, this item cannot be obtained through normal means, effectively removing this item.

### IsEnabled: [bool](data-types#bool)

If false, this item will be initially disabled. this item can be enabled or disabled manually in this item Options menu. If you're looking to effectively remove an item, use IsValid.

### LockedDD: [bool](data-types#bool)

If true, this item will be locked in shops in Dig Deep until either the blueprint is found or this item is equipped.

### LockedCR: [bool](data-types#bool)

If true, this item will be locked in shops in Creative until this item is equipped.

### LockedSU: [bool](data-types#bool)

If true, this item will be locked in shops in Survival until this item is equipped.

### MinCSPrice: [int](data-types#int)

The price this item sells for in the shop. this item can be bought for 120% of this price. 0 = Free, -1 = Unpurchasable. Note that setting the price to -1 will also remove this item from the creative inventory.

### StackSize: [int](data-types#int)

The maximum stack size of this item. If this item has durability, the stack size will always be 1.

### Durability: [ushort](data-types#ushort)

The durability of this item. If this is above 0, this item's stack size will always be 1.

### StrikeDamage: [float](data-types#float)

The base damage this item deals to targets when attacking.

### StrikeReach: [float](data-types#float)

The maximum distance this item can strike enemies at, in blocks.

### HealPower: [short](data-types#short)

The amount of health this item heals when used.

### BurnTime: [ushort](data-types#ushort)

The amount of time, in seconds, this item burns in a furnace.

### SmeltTime: [float](data-types#float)

The amount of time, in seconds, this item takes to be smelted in a furnace. If this item cannot be created in a furnace, this is ignored.

### ParticleLight: [byte](data-types#byte)

How much this item glows in the player's hand and on the ground. this item will not emit light.
- Valid Values: Between 0 and 15.

### CanDropIfLocked: [bool](data-types#bool)

If false, this item cannot be dropped by mobs unless this item has been unlocked.

### Plural: Plural

How the game displays this item's name in plural.
- Valid Values: None, S, ES

#### [Table of Contents](#adding-and-modifying-items)

---

## ItemTypeData.xml:

Contains information about this item's type data and use.

### ItemID: [Item](data-types#item)

The ID of this item. If this is an existing item, that item will be modified, otherwise this item will be added.

### Use: ItemUse

The use type of this item.
- Valid Values: Block, Item

### Type: ItemType

The type of this item.
- Valid Values: Block, Item, Tool, Weapon, Armor, Power, Food, Decor, Jewelry

### SubType: ItemSubType

The sub type of this item. An item can have multiple subtypes by separating value with spaces.
- Valid Values: Bow, Arrow, Shield, Edible, TillTool, HarvestTool, Grenade, GrenadeLauncher, Key, Door, RangedWeapon, BlockCanBeOpened, Leaves, Gun, RapidSwing, Potion

### ClassID: [ItemTypeClass](#itemtypeclassdataxml)

The class ID of this item. The class determines the power and maximum resistance of this item when mining. This can also be a custom class.
- Valid Values: None, CantMine, Wood, Bronze, Iron, Steel, GreenstoneGold, Platinum, Diamond, Ruby, Titanium, SledgeHammer

### Inv: ItemInvType

The shop tab this item will appear in.
- Valid Values: Blocks: Natural, Stone, Ore, Flora, Utility, Building | Items: Tool, Weapon, Armor, Food, Jewelry, Key, Other

### CombatID: [CombatItem](#itemcombatdataxml)

The combat ID for this item. The combat class determines the stat bonuses of this item. This can also be a custom combat class.
- Valid Values: Any item with stat bonuses

### Model: ItemModelType

This item's model type. The model type determines how this item looks when held.
- Valid Values: Block, IconBlock, BigIconBlock, Item, MediumItem, MediumItemFront, ItemTLBR, Tool, Hatchet, Weapon, WeaponTLBR, WeaponTRBL, BigWeapon, SteelScimitar, SteelClaymore, Bow, Arrow, Armor, Shield, Key, Jewelry, Door, Torch, GunHand, GunRifle, Clipboard, Staff

### Swing: [ItemSwingType](#itemswingdataxml)

this item's swing type. The swing type determines how this item looks when swung.
- Valid Values: Block, Item, IconBlock, Ramp, Weapon, WeaponTRBL, Spear, Bow, Shield, Eating, Arrow, SwitchArrow, GunHand, GunRifle, Key, Staff

### Equip: EquipIndex

The slot this item should be equipped in.
- Valid Values: Head, Neck, Body, Legs, Feet, LeftSide, RightSide, LeftHand, RightHand

#### [Table of Contents](#adding-and-modifying-items)

---

## ItemTypeClassData.xml:

Contains information about the this item class. The number of hits taken to destroy a block is equal to Block Resistance / Item Power × Tool Effectiveness. Eg. Rhyolite has a resistance of 7200, and a Titanium Pickaxe has a power of 1200, meaning it will take 6 hits to destroy Rhyolite with a Titanium Pickaxe.

### ClassID: ItemTypeClass

The ID of this class. No spaces are allowed. If this is an existing class, that class will be modified, otherwise the class will be added.

### Power: [ushort](data-types#ushort)

The amount of "damage" that items of this class deal to blocks when mining.

### MaxResistance: [ushort](data-types#ushort)

The maximum block resistance that items of this class can mine. Blocks with a higher resistance will be unmineable

#### [Table of Contents](#adding-and-modifying-items)

---

## ItemCombatData.xml:

Contains information about the stat bonuses of items. Every 100 points in a stat is equal to 1 skill level.

### CombatID: CombatItem

The ID of this combat class. No spaces are allowed. If this is an existing combat class, that combat class will be modified, otherwise the combat class will be added.

### Health: [short](data-types#short)

The amount of Health stat points this item gives when equipped.

### Attack: [short](data-types#short)

The amount of Attack stat points this item gives when equipped.

### Strength: [short](data-types#short)

The amount of Strength stat points this item gives when equipped.

### Defence: [short](data-types#short)

The amount of Defence stat points this item gives when equipped.

### Ranged: [short](data-types#short)

The amount of Ranged stat points this item gives when equipped.

### Looting: [short](data-types#short)

The amount of Looting stat points this item gives when equipped.

#### [Table of Contents](#adding-and-modifying-items)

---

## ItemSwingTimeData.xml:

Contains information about the swing time of this item. The Time field is the total amount of time this item takes to swing and is not affected by another other field. Say, Time=1, and Pause=0.5: this item will take 1 second to swing, half a second of which is spent paused.

### ItemID: [Item](data-types#item)

The ID of this item. If this is an existing item, that item will be modified.

### Time: [float](data-types#float)

The total time, in seconds, it takes to swing this item. Other time values are not added to this time.

### Pause: [float](data-types#float)

The amount of time, in seconds, this item stays in the rest position after being swung before being able to be swung again.

### ExtendedPause: [float](data-types#float)

The amount of time, in seconds, this item remains in its fully extended position.

### RetractTime: [float](data-types#float)

The amount of time, in seconds, this item takes to return to the rest position after reaching its fully extended position. Setting this to -1 makes this item retract in the same amount of time it takes to extend.

### RetractSmooth: [bool](data-types#bool)

If true, this item will retract smoothly.

#### [Table of Contents](#adding-and-modifying-items)

---

## ItemSwingData.xml:

Contains information about how items are swung.

### SwingID: ItemSwingType

The ID of this swing type. No spaces are allowed. Must be an existing swing type.
- Valid Values: None, Block, Item, IconBlock, Ramp, Weapon, WeaponTRBL, Spear, Bow, Shield, Eating, Arrow, SwitchArrow, GunHand, GunRifle, Key, Staff

### IsSwingable: [bool](data-types#bool)

If false, items with this swing type cannot be swung.

### SwingTime: [float](data-types#float)

The amount of time, in seconds, it takes to swing items with this swing type. Set this to 0 to use the time specified for the specific item.

### RestPosition: [Vector3](data-types#vector3)

The local position of this item when resting.

### RestRotation: [Vector3](data-types#vector3)

The rotation of this item when resting.

### ExtendedPosition: [Vector3](data-types#vector3)

The local position of this item when fully extended in third person.

### ExtendedPositionFPV: [Vector3](data-types#vector3)

The local position of this item when fully extended in first person.

### ExtendedRotation: [Vector3](data-types#vector3)

The rotation of this item when fully extended in third person.

### ExtendedRotationFPV: [Vector3](data-types#vector3)

The rotation of this item when fully extended in first person.

### CircularY: [float](data-types#float)

The maximum height of the circular vertical movement of this item while swinging in third person.

### CircularZ: [float](data-types#float)

The maximum circular forward movement of this item while swinging in both third and first person.

### CircularYFPV: [float](data-types#float)

The maximum height of the circular vertical movement of this item while swinging in first person.

#### [Table of Contents](#adding-and-modifying-items)

---

## ItemSoundData.xml:

Contains information about the sound this item makes.

### ItemID: [Item](data-types#item)

The ID of this item. If this is an existing item, that item will be modified.

### Group: ItemSoundGroup

The sound group of this item.
- Valid Values: None, Base, BodyHit, EnvNightfall, GenPickup, GuiAccept, GuiCancel, GuiInvalid, GuiMoveCursor, GuiSelect, GuiTransfer, GuiGamerJoined, GuiTxtMsgIn, ItemActivate, ItemArmor, ItemBlock, ItemBow, ItemCooked, ItemCrop, ItemDiamantiumTool, ItemDiamondTool, ItemWoodDoor, ItemMetalDoor, ItemEarth, ItemFire, ItemFlora, ItemGem, ItemGlass, ItemGrass, ItemGreenstoneTool, ItemIronTool, ItemJewelry, ItemKey, ItemLava, ItemLeather, ItemMetal, ItemOre, ItemPorous, ItemPortcullis, ItemRareTool, ItemRaw, ItemRock, ItemRope, ItemRubyTool, ItemSand, ItemShield, ItemSkill, ItemSnow, ItemSteelTool, ItemStone, ItemTile, ItemTitaniumTool, ItemTree, ItemWater, ItemWood, ItemWoodTool, ItemWool, ItemGun, ItemGunSMG, ItemGunLaser

### Sounds: ItemSoundXML

ItemSoundXML class specifying the sounds this items should make on certain actions.

#### [Table of Contents](#adding-and-modifying-items)

---

## SkillData.xml:

Contains information about the skill types and requirements for this item.

### ItemID: [Item](data-types#item)

The ID of this item. If this is an existing item, that item will be modified.

### MineReq: [int](data-types#int)

If this item is a block, the minimum skill level required to mine it.

### UseReq: [int](data-types#int)

The minimum skill level required to use this item.

### UseSkill: SkillType

The skill this item uses.
- Valid Values: Health, Strength, Attack, Defence, Ranged, Mining, Digging, Chopping, Building, Crafting, Smelting, Smithing, Farming, Cooking, Looting

### CraftReq: [int](data-types#int)

The minimum skill level reqiured to craft this item.

### CraftSkill: SkillType

The skill used to craft this item.
- Valid Values: Health, Strength, Attack, Defence, Ranged, Mining, Digging, Chopping, Building, Crafting, Smelting, Smithing, Farming, Cooking, Looting

#### [Table of Contents](#adding-and-modifying-items)

---

## BlueprintData.xml:

Contains information about how this item is crafted and its Dig Deep Blueprint.

### ItemID: [Item](data-types#item)

The ID of this item. Blueprints can only be added this way, not removed.

### CraftType: BlueprintCraftType

The method of which this item is crafted.
- Valid Values: Crafting, Furnace

### IsDefault: [bool](data-types#bool)

If true, this recipe will be automatically unlocked in Dig Deep without needing to find the blueprint.

### Depth: [Vector2](data-types#vector2)

The minimum and maximum depth percentage of this item's blueprint in Dig Deep. 0 = highest depth, 1 = lowest depth.

### Result: [InventoryItemNDXML](data-types#inventoryitemndxml)

The item this recipe crafts.

### Material11: [InventoryItemXML](data-types#inventoryitemxml)

The item to be placed in the bottom-left of the 3x3 crafting grid.

### Material12: [InventoryItemXML](data-types#inventoryitemxml)

The item to be placed in the bottom-middle of the 3x3 crafting grid.

### Material13: [InventoryItemXML](data-types#inventoryitemxml)

The item to be placed in the bottom-right of the 3x3 crafting grid.

### Material21: [InventoryItemXML](data-types#inventoryitemxml)

The item to be placed in the middle-left of the 3x3 crafting grid.

### Material22: [InventoryItemXML](data-types#inventoryitemxml)

The item to be placed in the middle of the 3x3 crafting grid.

### Material23: [InventoryItemXML](data-types#inventoryitemxml)

The item to be placed in the middle-right of the 3x3 crafting grid.

### Material31: [InventoryItemXML](data-types#inventoryitemxml)

The item to be placed in the top-left of the 3x3 crafting grid.

### Material32: [InventoryItemXML](data-types#inventoryitemxml)

The item to be placed in the top-middle of the 3x3 crafting grid.

### Material33: [InventoryItemXML](data-types#inventoryitemxml)

The item to be placed in the top-right of the 3x3 crafting grid.

#### [Table of Contents](#adding-and-modifying-items)

---

## ItemTextures16.xml/ItemTextures32.xml:

Contains the order of items in their respective texture atlas image. HD Texture Packs use ItemTextures32.xml while SD Texture Packs use ItemTextures16.xml. Always supply both TexturesXML files and both texture atlas images when adding custom items. The texture atlas image should have every item texture laid out next to one another. Recommended up to 32 items on one line in the texture atlas. Once the 32nd item is reached, move down a line.

### ItemID: [Item](data-types#item)

The ID of this item.

#### [Table of Contents](#adding-and-modifying-items)