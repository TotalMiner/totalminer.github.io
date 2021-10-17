
# (Official) LUA Scripting Documentation

## move_inventory_region

Move (transfer) all block inventories in a cubic region to another region.

___

Spec:

```lua
move_inventory_region(
	long x1,
	long y1,
	long z1,
	long x2,
	long y2,
	long z2,
	long x3,
	long y3,
	long z3,
	long item_id,
	long qty)
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
- `item_id`: The item_id to move. If omitted, all items will be moved
- `qty`: The quantity of the item to move. If omitted, all of the item will be moved

___

### Incomplete

documentation incomplete

___

### [back](../inventory)
