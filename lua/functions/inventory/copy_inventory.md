
# (Official) LUA Scripting Documentation

## copy_inventory

Copy a block's inventory to another voxel position.

___

Spec:

```lua
copy_inventory(
	x1,
	y1,
	z1,
	x2,
	y2,
	z2,
	item_id,
	qty)
```

## Parameters

- `x1:` The x component of the source block position
- `y1:` The y component of the source block position
- `z1:` The z component of the source block position
- `x2:` The x component of the destination block position
- `y2:` The y component of the destination block position
- `z2:` The z component of the destination block position
- `item_id:` The item_id to copy. If omitted, all items will be copied
- `qty:` The quantity of the item to copy. If omitted, all of the item will be copied

___

### [back](../inventory)
