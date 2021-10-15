
# (Official) LUA Scripting Documentation

## move_region
#
### Move block data (block id, aux, light) from one cubic region to another.
#
Spec:
```lua
move_region(
	x1,
	y1,
	z1,
	x2,
	y2,
	z2,
	x3,
	y3,
	z3)
```
#
## Parameters:
- `x1:` The x component of the source regions min position
- `y1:` The y component of the source regions min position
- `z1:` The z component of the source regions min position
- `x2:` The x component of the source regions max position
- `y2:` The y component of the source regions max position
- `z2:` The z component of the source regions max position
- `x3:` The x component of the destination regions min position
- `y3:` The y component of the destination regions min position
- `z3:` The z component of the destination regions min position
#
## Example
```lua
move_region(100,10,200,120,20,240,400,50,200)
```
This example moves the block id, aux data and light data of all the blocks in the region 100,10,200 to 120,20,240 to a region of the same size starting at 400,50,200.
#
### [back](../blocks)
