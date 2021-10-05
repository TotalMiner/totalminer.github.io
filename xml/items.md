# (Unofficial) XML Modding API Documentation

## Pages
- [Home](/index)
- [XML Documentation](/xml/xml-doc)
- [Data Types](/xml/data-types)
- [Adding and Modifying Items](/xml/items)
- [Modifying Blocks](/xml/blocks)
- [Adding and Modifying NPCs](/xml/npcs)

# Adding And Modifying Items

Items can be added and modified with XML mods. Items can be added and given properties, stat bonuses, item classes, and so on. If the ID supplied already exists, that item will be modified. Below is the documentation for each file used to add or modify items. Any file or field can be omitted for the item to use default values.
- [ItemData.xml](#itemdataxml)
- [ItemTypeData.xml](#itemtypedataxml)
- [ItemTypeClassData.xml](#itemtypeclassdataxml)
- [ItemCombatData.xml](#itemcombatdataxml)
- [ItemSwingTimeData.xml](#itemswingtimedataxml)
- [ItemSwingData.xml](#itemswingdataxml)
- [ItemSoundData.xml](#itemsounddataxml)
- [SkillData.xml](#skilldataxml)
- [BlueprintData.xml](#blueprintdataxml)
- [ItemTextures32.xml/ItemTexture16.xml](#itemtextures32xml/itemtexture16xml)

---

## ItemData.xml:

Contains general information about the item.

### ItemID: [Item](/xml/data-types#item)

The ID of the item. If this is an existing item, that item will be modified, otherwise the item will be added.

### Name: [string](/xml/data-types#string)

The name of the item that appears in the inventory, item interact screen, etc. The name can include spaces.

### Desc: [string](/xml/data-types#string)

The description of the item shown on the item interact screen.

### IsValid: [bool](/xml/data-types#bool)

If false, the item cannot be obtained through normal means, effectively removing the item.

### IsEnabled: [bool](/xml/data-types#bool)

If false, the item will be initially disabled. The item can be enabled or disabled manually in the Item Options menu. If you're looking to effectively remove an item, use IsValid.

### LockedDD: [bool](/xml/data-types#bool)

If true, the item will be locked in shops in Dig Deep until either the blueprint is found or the item is equipped.

### LockedCR: [bool](/xml/data-types#bool)

If true, the item will be locked in shops in Creative until the item is equipped.

### LockedSU: [bool](/xml/data-types#bool)

If true, the item will be locked in shops in Survival until the item is equipped.

### MinCSPrice: [int](/xml/data-types#int)

The price the item sells for in the shop. The item can be bought for 120% of this price. 0 = Free, -1 = Unpurchasable. Note that setting the price to -1 will also remove the item from the creative inventory.

### StackSize: [int](/xml/data-types#int)

The maximum stack size of the item. If the item has durability, the stack size will always be 1.

### Durability: [ushort](/xml/data-types#ushort)

The durability of the item. If this is above 0, the item's stack size will always be 1.

### StrikeDamage: [float](/xml/data-types#float)

The base damage the item deals to targets when attacking.

### StrikeReach: [float](/xml/data-types#float)

The maximum distance the item can strike enemies at, in blocks.

### HealPower: [short](/xml/data-types#short)

The amount of health the item heals when used.

### BurnTime: [ushort](/xml/data-types#ushort)

The amount of time, in seconds, the item burns in a furnace.

### SmeltTime: [float](/xml/data-types#float)

The amount of time, in seconds, the item takes to be smelted in a furnace. If the item cannot be created in a furnace, this is ignored.

### ParticleLight: [byte](/xml/data-types#byte)

How much the item glows in the player's hand and on the ground. The item will not emit light.
- Valid Values: Between 0 and 15.

### CanDropIfLocked: [bool](/xml/data-types#bool)

If false, the item cannot be dropped by mobs unless the item has been unlocked.

### Plural: Plural

How the game displays this item's name in plural.
- Valid Values: None, S, ES

#### [Table of Contents](#adding-and-modifying-items)

---

## ItemTypeData.xml:

Contains information about the item's type data and use.

### ItemID: [Item](/xml/data-types#item)

The ID of the item. If this is an existing item, that item will be modified, otherwise the item will be added.

### Use: ItemUse

The use type of the item.
- Valid Values: Block, Item

### Type: ItemType

The type of the item.
- Valid Values: Block, Item, Tool, Weapon, Armor, Power, Food, Decor, Jewelry

### SubType: ItemSubType

The sub type of the item. An item can have multiple subtypes by separating value with spaces.
- Valid Values: Bow, Arrow, Shield, Edible, TillTool, HarvestTool, Grenade, GrenadeLauncher, Key, Door, RangedWeapon, BlockCanBeOpened, Leaves, Gun, RapidSwing, Potion

### ClassID: ItemTypeClass

The class ID of the item. The class determines the power and maximum resistance of the item when mining. This can also be a custom class.
- Valid Values: None, CantMine, Wood, Bronze, Iron, Steel, GreenstoneGold, Platinum, Diamond, Ruby, Titanium, SledgeHammer

### Inv: ItemInvType

The shop tab this item will appear in.
- Valid Values: Blocks: Natural, Stone, Ore, Flora, Utility, Building | Items: Tool, Weapon, Armor, Food, Jewelry, Key, Other

### CombatID: CombatItem

The combat ID for the item. The combat class determines the stat bonuses of the item. This can also be a custom combat class.
- Valid Values: Any item with stat bonuses

### Model: ItemModelType

The item's model type. The model type determines how the weapon looks when held.
- Valid Values: Block, IconBlock, BigIconBlock, Item, MediumItem, MediumItemFront, ItemTLBR, Tool, Hatchet, Weapon, WeaponTLBR, WeaponTRBL, BigWeapon, SteelScimitar, SteelClaymore, Bow, Arrow, Armor, Shield, Key, Jewelry, Door, Torch, GunHand, GunRifle, Clipboard, Staff

### Swing: ItemSwingType

The item's swing type. The swing type determines how the looks when swung.
- Valid Values: Block, Item, IconBlock, Ramp, Weapon, WeaponTRBL, Spear, Bow, Shield, Eating, Arrow, SwitchArrow, GunHand, GunRifle, Key, Staff

### Equip: EquipIndex

The slot the item should be equipped in.
- Valid Values: Head, Neck, Body, Legs, Feet, LeftSide, RightSide, LeftHand, RightHand

#### [Table of Contents](#adding-and-modifying-items)

---

## ItemTypeClassData.xml:

Contains information about the the item class. The amount of hits taken to destroy a block is equal to Block Resistance / Item Power × Tool Effectiveness. Eg. Rhyolite has a resistance of 7200, and a Titanium Pickaxe has a power of 1200, meaning it will take 6 hits to destroy Rhyolite with a Titanium Pickaxe.

### ClassID: ItemTypeClass

The ID of this class. No spaces are allowed. If this is an existing class, that class will be modified, otherwise the class will be added.

### Power: [ushort](/xml/data-types#ushort)

The amount of "damage" an item with this class deals to blocks when mining.

### MaxResistance: [ushort](/xml/data-types#ushort)

The maximum block resistance that this class can mine. Blocks with a higher resistance will be unmineable

#### [Table of Contents](#adding-and-modifying-items)

---

## ItemCombatData.xml:

Contains information about the stat bonuses of items. Every 100 points in a stat is equal to 1 skill level.

### CombatID: CombatItem

The ID of this combat class. No spaces are allowed. If this is an existing combat class, that combat class will be modified, otherwise the combat class will be added.

### Health: [short](/xml/data-types#short)

The amount of Health stat points equipping this item adds.

### Attack: [short](/xml/data-types#short)

The amount of Attack stat points equipping this item adds.

### Strength: [short](/xml/data-types#short)

The amount of Strength stat points equipping this item adds.

### Defence: [short](/xml/data-types#short)

The amount of Defence stat points equipping this item adds.

### Ranged: [short](/xml/data-types#short)

The amount of Ranged stat points equipping this item adds.

### Looting: [short](/xml/data-types#short)

The amount of Looting stat points equipping this item adds.

#### [Table of Contents](#adding-and-modifying-items)

---

## ItemSwingTimeData.xml:

Contains information about the swing time of the item. The Time field is the total amount of time the item takes to swing and is not affected by another other field. Say, Time=1, and Pause=0.5: The item will take 1 second to swing, half a second of which is spent paused.

### ItemID: [Item](/xml/data-types#item)

The ID of this item. If this is an existing item, that item will be modified.

### Time: [float](/xml/data-types#float)

The total time, in seconds, it takes to swing the item. Other time values are not added to this time.

### Pause: [float](/xml/data-types#float)

The amount of time, in seconds, the item stays in the rest position after being swung before being able to be swung again.

### ExtendedPause: [float](/xml/data-types#float)

The amount of time, in seconds, the item remains in its fully extended position.

### RetractTime: [float](/xml/data-types#float)

The amount of time, in seconds, the item takes to return to the rest position after reaching its fully extended position. Setting this to -1 makes the item retract in the same amount of time it takes to extend.

### RetractSmooth: [bool](/xml/data-types#bool)

If true, the item will retract smoothly.

#### [Table of Contents](#adding-and-modifying-items)

---

## ItemSwingData.xml:

Contains information about how items are swung.

### SwingID: ItemSwingType

The ID of this swing type. No spaces are allowed. Must be an existing swing type.
- Valid Values: None, Block, Item, IconBlock, Ramp, Weapon, WeaponTRBL, Spear, Bow, Shield, Eating, Arrow, SwitchArrow, GunHand, GunRifle, Key, Staff

### IsSwingable: [bool](/xml/data-types#bool)

If false, the item cannot be swung.

### SwingTime: [float](/xml/data-types#float)

The amount of time, in seconds, the item takes to swing the item. Set this to 0 to use the time specified for the specific item.

### RestPosition: [Vector3](/xml/data-types#vector3)

The local position of the item when resting.

### RestRotation: [Vector3](/xml/data-types#vector3)

The rotation of the item when resting.

### ExtendedPosition: [Vector3](/xml/data-types#vector3)

The local position of the item when fully extended in third person.

### ExtendedPositionFPV: [Vector3](/xml/data-types#vector3)

The local position of the item when fully extended in first person.

### ExtendedRotation: [Vector3](/xml/data-types#vector3)

The rotation of the item when fully extended in third person.

### ExtendedRotationFPV: [Vector3](/xml/data-types#vector3)

The rotation of the item when fully extended in first person.

### CircularY: [float](/xml/data-types#float)

The maximum height of the circular vertical movement of the item while swinging in third person.

### CircularZ: [float](/xml/data-types#float)

The maximum circular forward movement of the item while swinging in both third and first person.

### CircularYFPV: [float](/xml/data-types#float)

The maximum height circular vertical movement of the item while swinging in first person.

#### [Table of Contents](#adding-and-modifying-items)

---

## ItemSoundData.xml:

Contains information about the sound the item makes.

### ItemID: [Item](/xml/data-types#item)

The ID of this item. If this is an existing item, that item will be modified.

### Group: ItemSoundGroup

The sound group of this item.
- Valid Values: None, Base, BodyHit, EnvNightfall, GenPickup, GuiAccept, GuiCancel, GuiInvalid, GuiMoveCursor, GuiSelect, GuiTransfer, GuiGamerJoined, GuiTxtMsgIn, ItemActivate, ItemArmor, ItemBlock, ItemBow, ItemCooked, ItemCrop, ItemDiamantiumTool, ItemDiamondTool, ItemWoodDoor, ItemMetalDoor, ItemEarth, ItemFire, ItemFlora, ItemGem, ItemGlass, ItemGrass, ItemGreenstoneTool, ItemIronTool, ItemJewelry, ItemKey, ItemLava, ItemLeather, ItemMetal, ItemOre, ItemPorous, ItemPortcullis, ItemRareTool, ItemRaw, ItemRock, ItemRope, ItemRubyTool, ItemSand, ItemShield, ItemSkill, ItemSnow, ItemSteelTool, ItemStone, ItemTile, ItemTitaniumTool, ItemTree, ItemWater, ItemWood, ItemWoodTool, ItemWool, ItemGun, ItemGunSMG, ItemGunLaser

### Sounds: ItemSoundXML

ItemSoundXML class specifying the sounds this items should make on certain actions.

#### [Table of Contents](#adding-and-modifying-items)

---

## SkillData.xml:

Contains information about the skill types and requirements for the item.

### ItemID: [Item](/xml/data-types#item)

The ID of this item. If this is an existing item, that item will be modified.

### MineReq: [int](/xml/data-types#int)

If this item is a block, the minimum mining level required to mine it.

### UseReq: [int](/xml/data-types#int)

The minimum skill level required to use this item.

### UseSkill: SkillType

The skill this item uses.
- Valid Values: Health, Strength, Attack, Defence, Ranged, Mining, Digging, Chopping, Building, Crafting, Smelting, Smithing, Farming, Cooking, Looting

### CraftReq: [int](/xml/data-types#int)

The minimum skill level reqiured to craft this item.

### CraftSkill: SkillType

The skill used to craft this item.
- Valid Values: Health, Strength, Attack, Defence, Ranged, Mining, Digging, Chopping, Building, Crafting, Smelting, Smithing, Farming, Cooking, Looting

#### [Table of Contents](#adding-and-modifying-items)

---

## BlueprintData.xml:

Contains information about how the item is crafted and its Dig Deep Blueprint.

### ItemID: [Item](/xml/data-types#item)

The ID of this item. Blueprints can only be added this way, not removed.

### CraftType: BlueprintCraftType

The method of which this item is crafted.
- Valid Values: Crafting, Furnace

### IsDefault: [bool](/xml/data-types#bool)

If true, this recipe will be automatically unlocked in Dig Deep without needing to find the blueprint.

### Depth: [Vector2](/xml/data-types#vector2)

The minimum and maximum depth percentage of the item's blueprint in Dig Deep. 0 = highest depth, 1 = lowest depth.

### Result: [InventoryItemNDXML](/xml/data-types#inventoryitemndxml)

The item this recipe crafts.

### Material11: [InventoryItemXML](/xml/data-types#inventoryitemxml)

The item to be placed in the bottom-left of the 3x3 crafting grid.

### Material12: [InventoryItemXML](/xml/data-types#inventoryitemxml)

The item to be placed in the bottom-middle of the 3x3 crafting grid.

### Material13: [InventoryItemXML](/xml/data-types#inventoryitemxml)

The item to be placed in the bottom-right of the 3x3 crafting grid.

### Material21: [InventoryItemXML](/xml/data-types#inventoryitemxml)

The item to be placed in the middle-left of the 3x3 crafting grid.

### Material22: [InventoryItemXML](/xml/data-types#inventoryitemxml)

The item to be placed in the middle of the 3x3 crafting grid.

### Material23: [InventoryItemXML](/xml/data-types#inventoryitemxml)

The item to be placed in the middle-right of the 3x3 crafting grid.

### Material31: [InventoryItemXML](/xml/data-types#inventoryitemxml)

The item to be placed in the top-left of the 3x3 crafting grid.

### Material32: [InventoryItemXML](/xml/data-types#inventoryitemxml)

The item to be placed in the top-middle of the 3x3 crafting grid.

### Material33: [InventoryItemXML](/xml/data-types#inventoryitemxml)

The item to be placed in the top-right of the 3x3 crafting grid.

#### [Table of Contents](#adding-and-modifying-items)

---

## ItemTextures32.xml/ItemTexture16.xml:

Contains the order of items in their respective texture atlas image. HD Texture Packs use ItemTextures32.xml while SD Texture Packs use ItemTextures16.xml. Always supply both TexturesXML files and both texture atlas images when adding custom items. The texture atlas image should have every item texture laid out next to one another. Recommended up to 32 items on one line in the texture atlas. Once the 32nd item is reached, move down a line.

### ItemID: [Item](/xml/data-types#item)

The ID of the item.