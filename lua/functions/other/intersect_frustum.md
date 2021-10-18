
# (Official) LUA Scripting Documentation

## intersect_frustum

Frustum intersection query.

___

Spec:

```lua
intersect_frustum(
	double x1,
	double y1,
	double z1,
	double x2,
	double y2,
	double z2,
	long fov,
	bool players,
	bool npcs,
	bool display)
```

## Parameters

- `x1`: The x component of the world position at the center of the frustum near plane
- `y1`: The y component of the world position at the center of the frustum near plane
- `z1`: The z component of the world position at the center of the frustum near plane
- `x2`: The x component of the world position at the center of the frustum far plane
- `y2`: The y component of the world position at the center of the frustum far plane
- `z2`: The z component of the world position at the center of the frustum far plane
- `fov`: The field of view of the frustum specified in degrees. If omitted, the default is 60
- `players`: true = test for players, false = do not test for players. If omitted, the default is true
- `npcs`: true = test for NPCs, false = do not test for NPCs. If omitted, the default is true
- `display`: true = display an outline showing the frustum of the test. If omitted, the default is false

## Returns

- `bool`: True if there is at least one players/NPC positioned within the frustum

___

The context target is set as the closest actor inside the frustum

___

## Example

```lua
local dir = vector3(get_view_dir())
local near = vector3(get_eye_pos()) + (dir * 0.2)
local far = near + (dir * 50)
if intersect_frustum(near.x,near.y,near.z,far.x,far.y,far.z,60)
then
set_context("target")
add_health_effect(-10)
end
```

___

##### Incomplete

This documentation is incomplete

___

### [back](../other)
