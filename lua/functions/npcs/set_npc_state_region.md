
# (Official) LUA Scripting Documentation

## set_npc_state_region

Set the state of all NPCs in a cubic region.

___

Spec:

```lua
set_npc_state_region(
	state,
	x1,
	y1,
	z1,
	x2,
	y2,
	z2,
	npc_type)
```

## Parameters

- `state:` 
- `x1:` The x component of the regions min position
- `y1:` The y component of the regions min position
- `z1:` The z component of the regions min position
- `x2:` The x component of the regions max position
- `y2:` The y component of the regions max position
- `z2:` The z component of the regions max position
- `npc_type:` Only apply to these types of NPCs. Omit to apply to all types of NPCs

___

### [back](../npcs)
