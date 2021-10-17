
# (Official) LUA Scripting Documentation

## get_npc_count_in_region

Get the total number of NPCs currently positioned inside a cubic region.

___

Spec:

```lua
get_npc_count_in_region(
	long x1,
	long y1,
	long z1,
	long x2,
	long y2,
	long z2,
	string npc_type)
```

## Parameters

- `x1`: The x component of the regions min world point
- `y1`: The y component of the regions min world point
- `z1`: The z component of the regions min world point
- `x2`: The x component of the regions max world point
- `y2`: The y component of the regions max world point
- `z2`: The z component of the regions max world point
- `npc_type`: The type of NPC to count. Omit to count all NPCs

## Returns

- `long`: The count of NPCs

___

### Incomplete

documentation incomplete

___

### [back](../getters)
