
# (Official) LUA Scripting Documentation

## get_skill_level

Get the current level of a specified skill of the context actor.

___

Spec:

```lua
get_skill_level(
	string skill)
```

## Parameters

- `skill`: 

## Returns

- `long`: The skill level

___

Valid values for skill:
"Health", "Strength", "Attack", "Defence", "Ranged", "Mining", "Digging", "Chopping",
"Building", "Crafting", "Smelting", "Smithing", "Farming", "Cooking", "Looting"

___

## Example

```lua
local lvl = get_skill_level("attack")
```

___

##### Incomplete

This documentation is incomplete

___

### [back](../getters)
