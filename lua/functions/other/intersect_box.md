
# (Official) LUA Scripting Documentation

## intersect_box

Box (cubic region) intersection query.

___

Spec:

```lua
intersect_box(
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

- `x1`: The x component of the box (region) min world position
- `y1`: The y component of the box (region) min world position
- `z1`: The z component of the box (region) min world position
- `x2`: The x component of the box (region) max world position
- `y2`: The y component of the box (region) max world position
- `z2`: The z component of the box (region) max world position
- `players`: true = test for players, false = do not test for players. If omitted, the default is true
- `npcs`: true = test for NPCs, false = do not test for NPCs. If omitted, the default is true
- `display`: true = display an outline showing the box region of the test. If omitted, the default is false

## Returns

- `bool`: True if there is at least one players/NPC positioned within the box region

___

The context target is set as the closest actor inside the box

___

### Incomplete

This documentation is incomplete

___

### [back](../other)
