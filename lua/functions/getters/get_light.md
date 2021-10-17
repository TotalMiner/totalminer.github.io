
# (Official) LUA Scripting Documentation

## get_light

Get full light data of a map point.

___

Spec:

```lua
get_light(
	long x,
	long y,
	long z)
```

## Parameters

- `x`: The x component of the map point.
- `y`: The y component of the map point.
- `z`: The z component of the map point.

## Returns

- `long`: Light data is currently 8 bits. The first 4 bits are the sunlight, the 2nd 4 bits are the block light

___

## Example

```lua
local x,y,z = get_script_point()
if get_light(x,y+1,z) > 0 then notify("The map point above the script block has some light") end
```

___

### Incomplete

This documentation is incomplete

___

### [back](../getters)
