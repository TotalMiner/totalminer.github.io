
# (Official) LUA Scripting Documentation

## add_skill_level

Raise or lower a skill level of the context actor.

___

Spec:

```lua
add_skill_level(
	string skill,
	long level)
```

## Parameters

- `skill`: The skill to change
- `level`: The number of levels to add (positive number) or subtract (negative number). If omitted, one level will be added

___

Valid values for skill:
"Health", "Strength", "Attack", "Defence", "Ranged", "Mining", "Digging", "Chopping",
"Building", "Crafting", "Smelting", "Smithing", "Farming", "Cooking", "Looting"

___

##### Incomplete

This documentation is incomplete

___

### [back](../other)
