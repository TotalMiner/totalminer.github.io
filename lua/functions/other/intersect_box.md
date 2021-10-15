
# (Official) LUA Scripting Documentation

## intersect_box

### Box (cubic region) intersection query.

Spec:
```lua
intersect_box(
	x1,
	y1,
	z1,
	x2,
	y2,
	z2,
	players,
	npcs,
	display)
```
## Parameters:
- `x1:` The x component of the box (region) min position
- `y1:` The y component of the box (region) min position
- `z1:` The z component of the box (region) min position
- `x2:` The x component of the box (region) max position
- `y2:` The y component of the box (region) max position
- `z2:` The z component of the box (region) max position
- `players:` true = test for players, false = do not test for players. If omitted, the default is true
- `npcs:` true = test for NPCs, false = do not test for NPCs. If omitted, the default is true
- `display:` true = display an outline showing the box region of the test. If omitted, the default is false

## Returns:
- `bool:` True if there is at least one players/NPC positioned within the box region

The context target is set as the closest actor inside the box

### [back](../other)
