
# (Official) LUA Scripting Documentation

## get_gamer_count_in_radius

Get the total number of enabled gamers currently positioned inside a spherical region.

___

Spec:

```lua
get_gamer_count_in_radius(
	long x,
	long y,
	long z,
	double radius)
```

## Parameters

- `x`: The x component of the world point at the center of the sphere.
- `y`: The y component of the world point at the center of the sphere.
- `z`: The z component of the world point at the center of the sphere.
- `radius`: 

## Returns

- `long`: The number of gamers

___

## Example

```lua
local x,y,z = get_pos()
local gamer_count = get_gamer_count_in_radius(x,y,z,100)
```

___

### Incomplete

This documentation is incomplete

___

### [back](../getters)
