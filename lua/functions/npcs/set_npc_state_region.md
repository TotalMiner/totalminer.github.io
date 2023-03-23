
# (Official) LUA Scripting Documentation

## set_npc_state_region

Set the state of all NPCs in a cubic region.

___

Spec:

```lua
set_npc_state_region(
	string state,
	long x1,
	long y1,
	long z1,
	long x2,
	long y2,
	long z2,
	string npc_type)
```

## Parameters

- `state`: 
- `x1`: The x component of the regions min map point
- `y1`: The y component of the regions min map point
- `z1`: The z component of the regions min map point
- `x2`: The x component of the regions max map point
- `y2`: The y component of the regions max map point
- `z2`: The z component of the regions max map point
- `npc_type`: Only apply to these types of NPCs. Omit to apply to all types of NPCs

___

Valid values for state:
"alive", "dying", "death", "respawning", "respawn", "despawning",
"despawn", "sleeping", "sleep", "custom", "inactive", "delete"

___

##### Incomplete

This documentation is incomplete

___

### [back](../npcs)
