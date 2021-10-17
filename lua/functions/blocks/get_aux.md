
# (Official) LUA Scripting Documentation

## get_aux

Get the aux data at a map point.

___

Spec:

```lua
get_aux(
	long x,
	long y,
	long z)
```

## Parameters

- `x`: The x component of the map point
- `y`: The y component of the map point
- `z`: The z component of the map point

## Returns

- `long`: The aux data. Currently only the first 8 bits of aux data is used

___

## Example

```lua
local x,y,z = get_script_point()
local aux = get_aux(x,y,z)
```

This example gets the aux data of the script block that executed this script.

___

### Incomplete

documentation incomplete

___

### [back](../blocks)
