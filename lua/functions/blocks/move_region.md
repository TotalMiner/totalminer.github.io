
# (Official) LUA Scripting Documentation

## move_region

Move block data (block id, aux, light) from one cubic region to another.

___

Spec:

```lua
move_region(
	long x1,
	long y1,
	long z1,
	long x2,
	long y2,
	long z2,
	long x3,
	long y3,
	long z3)
```

## Parameters

- `x1`: The x component of the source regions min map point
- `y1`: The y component of the source regions min map point
- `z1`: The z component of the source regions min map point
- `x2`: The x component of the source regions max map point
- `y2`: The y component of the source regions max map point
- `z2`: The z component of the source regions max map point
- `x3`: The x component of the destination regions min map point
- `y3`: The y component of the destination regions min map point
- `z3`: The z component of the destination regions min map point

___

## Example

```lua
move_region(100,10,200,120,20,240,400,50,200)
```

This example moves the block id, aux data and light data of all the blocks in the region 100,10,200 to 120,20,240 to a region of the same size starting at 400,50,200.

___

### Incomplete

documentation incomplete

___

### [back](../blocks)
