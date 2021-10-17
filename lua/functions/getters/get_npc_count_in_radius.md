
# (Official) LUA Scripting Documentation

## get_npc_count_in_radius

Get the total number of NPCs currently positioned inside a spherical region.

___

Spec:

```lua
get_npc_count_in_radius(
	long x,
	long y,
	long z,
	double radius,
	string npc_type)
```

## Parameters

- `x`: The x component of the map point at the center of the sphere.
- `y`: The y component of the map point at the center of the sphere.
- `z`: The z component of the map point at the center of the sphere.
- `radius`: 
- `npc_type`: The type of NPC to count. Omit to count all NPCs

## Returns

- `long`: The count of NPCs

___

#### Incomplete

This documentation is incomplete

___

### [back](../getters)
