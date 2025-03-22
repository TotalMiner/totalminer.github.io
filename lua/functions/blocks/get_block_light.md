
# (Official) LUA Scripting Documentation

## get_block_light

Get the amount of block emitted light at a map point.

___

Spec:

```lua
get_block_light(
	long x,
	long y,
	long z)
```

## Parameters

- `x`: The x component of the map point.
- `y`: The y component of the map point.
- `z`: The z component of the map point.

## Returns

- `long`: A value from 0 to 15. 0 = no light. 15 = max light

___

## Example

```lua
local x,y,z = get_script_point()
if get_block_light(x,y+1,z) > 8 then notify("It is quite light here") end
```

___

##### Incomplete

This documentation is incomplete

___

### [back](../blocks)
