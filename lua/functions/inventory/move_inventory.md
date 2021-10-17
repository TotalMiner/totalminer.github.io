
# (Official) LUA Scripting Documentation

## move_inventory

Move (transfer) a block inventory to another block.

___

Spec:

```lua
move_inventory(
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
- `item_id`: The item_id to move. If omitted, all items will be moved
- `qty`: The quantity of the item to move. If omitted, all of the item will be moved

___

### Incomplete

This documentation is incomplete

___

### [back](../inventory)
