
# (Official) LUA Scripting Documentation

## blueprint

Define a blueprint (crafting recipe) for an item.

___

Spec:

```lua
blueprint(
	item_id,
	qty,
	craft_type,
	craft_skill_type,
	craft_skill_level,
	smelt_time)
```

## Parameters

- `item_id`: The target item
- `qty`: The number of units crafted
- `craft_type`: Craft or Smelt
- `craft_skill_type`: The skill type required to craft the item
- `craft_skill_level`: The skill level (of the skill type) required to craft the item
- `smelt_time`: If the item is smelted, this is the time it takes to smelt the item in milliseconds

___

### [back](../other)
