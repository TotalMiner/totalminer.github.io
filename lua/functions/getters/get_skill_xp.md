
# (Official) LUA Scripting Documentation

## get_skill_xp

Get the current xp of a specified skill of the context actor.

___

Spec:

```lua
get_skill_xp(
	string skill)
```

## Parameters

- `skill`: 

## Returns

- `double`: The skill xp (experience points)

___

Valid values for skill:
"Health", "Strength", "Attack", "Defence", "Ranged", "Mining", "Digging", "Chopping",
"Building", "Crafting", "Smelting", "Smithing", "Farming", "Cooking", "Looting"

___

## Example

```lua
local xp = get_skill_xp("mining")
```

___

##### Incomplete

This documentation is incomplete

___

### [back](../getters)
