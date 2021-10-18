
# (Official) LUA Scripting Documentation

## cctv_at

Open a CCTV (targeted) for the context player.

___

Spec:

```lua
cctv_at(
	bool is_admin,
	long x1,
	long y1,
	long z1,
	long x2,
	long y2,
	long z2,
	long millisecs,
	double swivel_speed,
	long fov)
```

## Parameters

- `is_admin`: true = only admins can use this CCTV, false = all players can use it
- `x1`: The x component of the map point of the camera.
- `y1`: The y component of the map point of the camera.
- `z1`: The z component of the map point of the camera.
- `x2`: The x component of the target map point of the camera.
- `y2`: The y component of the target map point of the camera.
- `z2`: The z component of the target map point of the camera.
- `millisecs`: The duration of the CCTV in milliseconds
- `swivel_speed`: The speed at which the camera can be swivelled as a percentage. If omitted the default speed is 50%
- `fov`: The field of view of the camera specified in degrees. If omitted the default value is 80

___

##### Incomplete

This documentation is incomplete

___

### [back](../other)
