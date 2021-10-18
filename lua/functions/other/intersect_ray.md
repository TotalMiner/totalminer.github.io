
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
- `x2`: The x component of the world position of the end of the ray
- `y2`: The y component of the world position of the end of the ray
- `z2`: The z component of the world position of the end of the ray
- `players`: true = test for players, false = do not test for players. If omitted, the default is true
- `npcs`: true = test for NPCs, false = do not test for NPCs. If omitted, the default is true
- `display`: true = display an outline showing the ray of the test. If omitted, the default is false

## Returns

- `bool`: True if the ray intersects at least one players/NPC

___

The context target is set as the closest actor hit by the ray

___

## Example

```lua
local dir = vector3(get_view_dir())
local eye = vector3(get_eye_pos()) + (dir * 0.2)
local far = eye + (dir * 50)
if
intersect_ray(eye.x, eye.y, eye.z, far.x, far.y, far.z)
then
set_context("target")
add_health_effect(-30)
end
```

___

##### Incomplete

This documentation is incomplete

___

### [back](../other)
