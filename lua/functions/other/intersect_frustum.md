
# (Official) LUA Scripting Documentation

## intersect_frustum
#
### Frustum intersection query.
#
Spec:
```lua
intersect_frustum(
	x1,
	y1,
	z1,
	x2,
	y2,
	z2,
	fov,
	players,
	npcs,
	display)
```
#
## Parameters:
- `x1:` The x component of the (position) center of the frustum near plane
- `y1:` The y component of the (position) center of the frustum near plane
- `z1:` The z component of the (position) center of the frustum near plane
- `x2:` The x component of the (position) center of the frustum far plane
- `y2:` The y component of the (position) center of the frustum far plane
- `z2:` The z component of the (position) center of the frustum far plane
- `fov:` The field of view of the frustum specified in degrees. If omitted, the default is 60
- `players:` true = test for players, false = do not test for players. If omitted, the default is true
- `npcs:` true = test for NPCs, false = do not test for NPCs. If omitted, the default is true
- `display:` true = display an outline showing the frustum of the test. If omitted, the default is false
#
## Returns:
- `bool:` True if there is at least one players/NPC positioned within the frustum
#
The context target is set as the closest actor inside the frustum
#
### [back](../other)
