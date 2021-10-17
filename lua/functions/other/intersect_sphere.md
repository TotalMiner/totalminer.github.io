
# (Official) LUA Scripting Documentation

## intersect_sphere

Sphere intersection query.

___

Spec:

```lua
intersect_sphere(
	double x,
	double y,
	double z,
	double radius,
	bool players,
	bool npcs,
	bool display)
```

## Parameters

- `x`: The x component of the world position at the center of the sphere.
- `y`: The y component of the world position at the center of the sphere.
- `z`: The z component of the world position at the center of the sphere.
- `radius`: The radius of the sphere specified in blocks
- `players`: true = test for players, false = do not test for players. If omitted, the default is true
- `npcs`: true = test for NPCs, false = do not test for NPCs. If omitted, the default is true
- `display`: true = display an outline showing the sphere of the test. If omitted, the default is false

## Returns

- `bool`: True if there is at least one players/NPC positioned within the sphere

___

The context target is set as the closest actor inside the sphere

___

#### Incomplete

This documentation is incomplete

___

### [back](../other)
