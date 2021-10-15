
# (Official) LUA Scripting Documentation

## cctv

### Open a CCTV (directional) for the context player.

Spec:
```lua
cctv(
	is_admin,
	x,
	y,
	z,
	dir,
	millisecs,
	swivel_speed,
	fov)
```
## Parameters:
- `is_admin:` true = only admins can use this CCTV, false = all players can use it
- `x:` The x component of the position of the camera.
- `y:` The y component of the position of the camera.
- `z:` The z component of the position of the camera.
- `dir:` The direction the CCTV is facing - N, S, E or W
- `millisecs:` The duration of the CCTV in milliseconds
- `swivel_speed:` The speed at which the camera can be swivelled as a percentage. If omitted the default speed is 50%
- `fov:` The field of view of the camera specified in degrees. If omitted the default value is 80
### [back](../other)
