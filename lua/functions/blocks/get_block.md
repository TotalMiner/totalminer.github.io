
# (Official) LUA Scripting Documentation

## get_block

Get the block id at a map point.

___

Spec:

```lua
get_block(
	long x,
	long y,
	long z)
```

## Parameters

- `x`: The x component of the map point
- `y`: The y component of the map point
- `z`: The z component of the map point

## Returns

- `long`: The block id. Currently block ids are 8 bit integers

___

## Example

```lua
local x,y,z = get_script_point()
local block_id = get_block(x,y+1,z)
```

This example gets the block id of the block directly above the script block that executed this script.

___

### Incomplete

This documentation is incomplete

___

### [back](../blocks)
