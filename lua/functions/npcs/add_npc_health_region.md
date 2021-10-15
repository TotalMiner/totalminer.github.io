
# (Official) LUA Scripting Documentation

## add_npc_health_region
#
### Add or subtract to/from the health of all NPCs in a cubic region.
#
Spec:
```lua
add_npc_health_region(
	points,
	x1,
	y1,
	z1,
	x2,
	y2,
	z2,
	npc_type,
	millisecs,
	duration)
```
#
## Parameters:
- `points:` How many hitpoints to add. Use a negative number to subtract from (damage) the NPCs health
- `x1:` The x component of the regions min position
- `y1:` The y component of the regions min position
- `z1:` The z component of the regions min position
- `x2:` The x component of the regions max position
- `y2:` The y component of the regions max position
- `z2:` The z component of the regions max position
- `npc_type:` Only apply to these types of NPCs. Omit to apply to all types of NPCs
- `millisecs:` 
- `duration:` 
#
### [back](../npcs)
