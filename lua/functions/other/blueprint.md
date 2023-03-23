
# (Official) LUA Scripting Documentation

## blueprint

Define a blueprint (crafting recipe) for an item.

___

Spec:

```lua
blueprint(
	long item_id,
	long qty,
	string craft_type,
	string craft_skill_type,
	long craft_skill_level,
	double smelt_time)
```

## Parameters

- `item_id`: The target item
- `qty`: The number of units crafted
- `craft_type`: Craft or Smelt
- `craft_skill_type`: The skill type required to craft the item
- `craft_skill_level`: The skill level (of the skill type) required to craft the item
- `smelt_time`: If the item is smelted, this is the time it takes to smelt the item in milliseconds

___

## Example

```lua
Valid values for craft_type: "craft", "furnace"

Valid values for craft_skill_type:
"Health", "Strength", "Attack", "Defence", "Ranged", "Mining", "Digging", "Chopping",
"Building", "Crafting", "Smelting", "Smithing", "Farming", "Cooking", "Looting"
```

___

##### Incomplete

This documentation is incomplete

___

### [back](../other)
