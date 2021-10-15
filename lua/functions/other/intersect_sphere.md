
# (Official) LUA Scripting Documentation

## intersect_sphere
#
### Sphere intersection query.
#
Spec:
```lua
intersect_sphere(
	x,
	y,
	z,
	radius,
	players,
	npcs,
	display)
```
#
## Parameters:
- `x:` The x component of the position of the center of the sphere.
- `y:` The y component of the position of the center of the sphere.
- `z:` The z component of the position of the center of the sphere.
- `radius:` The radius of the sphere specified in blocks
- `players:` true = test for players, false = do not test for players. If omitted, the default is true
- `npcs:` true = test for NPCs, false = do not test for NPCs. If omitted, the default is true
- `display:` true = display an outline showing the sphere of the test. If omitted, the default is false
#  

## Returns:
- `bool:` True if there is at least one players/NPC positioned within the sphere
#
The context target is set as the closest actor inside the sphere
#
### [back](../other)
