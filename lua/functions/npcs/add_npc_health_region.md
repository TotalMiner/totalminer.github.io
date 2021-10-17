
# (Official) LUA Scripting Documentation

## add_npc_health_region

Add or subtract to/from the health of all NPCs in a cubic region.

___

Spec:

```lua
add_npc_health_region(
	long points,
	long x1,
	long y1,
	long z1,
	long x2,
	long y2,
	long z2,
	string npc_type,
	long millisecs,
	long duration)
```

## Parameters

- `points`: How many hitpoints to add. Use a negative number to subtract from (damage) the NPCs health
- `x1`: The x component of the regions min map point
- `y1`: The y component of the regions min map point
- `z1`: The z component of the regions min map point
- `x2`: The x component of the regions max map point
- `y2`: The y component of the regions max map point
- `z2`: The z component of the regions max map point
- `npc_type`: Only apply to these types of NPCs. Omit to apply to all types of NPCs
- `millisecs`: 
- `duration`: 

___

### Incomplete

documentation incomplete

___

### [back](../npcs)
