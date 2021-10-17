
# (Official) LUA Scripting Documentation

## intersect_ray

Ray intersection query.

___

Spec:

```lua
intersect_ray(
	double x1,
	double y1,
	double z1,
	double x2,
	double y2,
	double z2,
	bool players,
	bool npcs,
	bool display)
```

## Parameters

- `x1`: The x component of the world position of the origin of the ray
- `y1`: The y component of the world position of the origin of the ray
- `z1`: The z component of the world position of the origin of the ray
- `x2`: The x component of the direction of the ray
- `y2`: The y component of the direction of the ray
- `z2`: The z component of the direction of the ray
- `players`: true = test for players, false = do not test for players. If omitted, the default is true
- `npcs`: true = test for NPCs, false = do not test for NPCs. If omitted, the default is true
- `display`: true = display an outline showing the ray of the test. If omitted, the default is false

## Returns

- `bool`: True if the ray intersects at least one players/NPC

___

The context target is set as the closest actor hit by the ray

___

### Incomplete

documentation incomplete

___

### [back](../other)
