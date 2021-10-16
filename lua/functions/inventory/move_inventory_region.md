
# (Official) LUA Scripting Documentation

## move_inventory_region

Move (transfer) all block inventories in a cubic region to another region.

___

Spec:

```lua
move_inventory_region(
	x1,
	y1,
	z1,
	x2,
	y2,
	z2,
	x3,
	y3,
	z3,
	item_id,
	qty)
```

## Parameters

- `x1`: The x component of the source regions min position
- `y1`: The y component of the source regions min position
- `z1`: The z component of the source regions min position
- `x2`: The x component of the source regions max position
- `y2`: The y component of the source regions max position
- `z2`: The z component of the source regions max position
- `x3`: The x component of the destination regions min position
- `y3`: The y component of the destination regions min position
- `z3`: The z component of the destination regions min position
- `item_id`: The item_id to move. If omitted, all items will be moved
- `qty`: The quantity of the item to move. If omitted, all of the item will be moved

___

### [back](../inventory)
