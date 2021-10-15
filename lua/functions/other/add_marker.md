
# (Official) LUA Scripting Documentation

## add_marker
#
### Add a marker to the top down map.
#
Spec:
```lua
add_marker(
	name,
	x,
	z,
	is_admin)
```
#
## Parameters:
- `name:` The name (and text) of the marker
- `x:` The x component of the world position of the marker
- `z:` The z component of the world position of the marker
- `is_admin:` true or false. If true, only admins can see the marker
#
No y component is required because there is no height associated with markers, i.e. markers are positioned on the world surface
#
## Example
```lua
add_marker("Boat Ramp", 220, 400)
```
This example adds a marker 'Boat Ramp' to the world at surface position 220, 400. All players can see this marker
#
### [back](../other)
