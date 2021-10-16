
# (Official) LUA Scripting Documentation

## cctv_at

Open a CCTV (targeted) for the context player.

___

Spec:

```lua
cctv_at(
	is_admin,
	x1,
	y1,
	z1,
	x2,
	y2,
	z2,
	millisecs,
	swivel_speed,
	fov)
```

## Parameters

- `is_admin`: true = only admins can use this CCTV, false = all players can use it
- `x1`: The x component of the position of the camera.
- `y1`: The y component of the position of the camera.
- `z1`: The z component of the position of the camera.
- `x2`: The x component of the target position of the camera.
- `y2`: The y component of the target position of the camera.
- `z2`: The z component of the target position of the camera.
- `millisecs`: The duration of the CCTV in milliseconds
- `swivel_speed`: The speed at which the camera can be swivelled as a percentage. If omitted the default speed is 50%
- `fov`: The field of view of the camera specified in degrees. If omitted the default value is 80

___

### [back](../other)
