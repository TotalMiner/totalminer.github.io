
# (Official) LUA Scripting Documentation

## get_sun_light

Get the amount of sunlight at a world point.

___

Spec:

```lua
get_sun_light(
	long x,
	long y,
	long z)
```

## Parameters

- `x`: The x component of the map point.
- `y`: The y component of the map point.
- `z`: The z component of the map point.

## Returns

- `long`: The amount of sunlight at the specified point. Sunlight can be a value from 0 (no light) to 15 (max light)

___

## Example

```lua
local x,y,z = get_script_pos()
local sunlight = get_sun_light(x,y+1,z)
```

This example gets the amount of sunlight at the point directly above the script block that executed the script

___

#### Incomplete

This documentation is incomplete

___

### [back](../getters)
