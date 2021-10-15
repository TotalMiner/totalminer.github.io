
# (Official) LUA Scripting Documentation

## get_block
#
### Get the block id at a voxel position.
#
Spec:
```lua
get_block(
	x,
	y,
	z)
```
#
## Parameters:
- `x:` The x component of the position
- `y:` The y component of the position
- `z:` The z component of the position
#  

## Returns:
- `long:` The block id. Currently block ids are 8 bit integers
#
## Example
```lua
local x,y,z = get_script_point()
local block_id = get_block(x,y+1,z)
```
This example gets the block id of the block directly above the script block that executed this script.
#
### [back](../blocks)
