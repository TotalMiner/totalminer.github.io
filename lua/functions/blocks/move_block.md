
# (Official) LUA Scripting Documentation

## move_block

Move block data (block id, aux, light) from one voxel position to another.

___

Spec:

```lua
move_block(
	x1,
	y1,
	z1,
	x2,
	y2,
	z2)
```

## Parameters

- `x1`: The x component of the source position
- `y1`: The y component of the source position
- `z1`: The z component of the source position
- `x2`: The x component of the destination position
- `y2`: The y component of the destination position
- `z2`: The z component of the destination position

___

## Example

```lua
local x,y,z = get_script_point()
move_block(x,y,z,x,y+1,z)
```

This example moves the block id, aux data and light data of the script block that executed this script to the position directly above it.

___

### [back](../blocks)
