
# (Official) LUA Scripting Documentation

## move_block

Move block data (block id, aux, light) from one map point to another.

___

Spec:

```lua
move_block(
	long x1,
	long y1,
	long z1,
	long x2,
	long y2,
	long z2)
```

## Parameters

- `x1`: The x component of the source map point
- `y1`: The y component of the source map point
- `z1`: The z component of the source map point
- `x2`: The x component of the destination map point
- `y2`: The y component of the destination map point
- `z2`: The z component of the destination map point

___

## Example

```lua
local x,y,z = get_script_point()
move_block(x,y,z,x,y+1,z)
```

This example moves the block id, aux data and light data of the script block that executed this script to the point directly above it.

___

### Incomplete

This documentation is incomplete

___

### [back](../blocks)
