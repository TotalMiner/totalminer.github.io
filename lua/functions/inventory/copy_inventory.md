
# (Official) LUA Scripting Documentation

## copy_inventory

Copy a block's inventory to another block.

___

Spec:

```lua
copy_inventory(
	long x1,
	long y1,
	long z1,
	long x2,
	long y2,
	long z2,
	long item_id,
	long qty)
```

## Parameters

- `x1`: The x component of the source block map point
- `y1`: The y component of the source block map point
- `z1`: The z component of the source block map point
- `x2`: The x component of the destination block map point
- `y2`: The y component of the destination block map point
- `z2`: The z component of the destination block map point
- `item_id`: The item_id to copy. If omitted, all items will be copied
- `qty`: The quantity of the item to copy. If omitted, all of the item will be copied

___

##### Incomplete

This documentation is incomplete

___

### [back](../inventory)
