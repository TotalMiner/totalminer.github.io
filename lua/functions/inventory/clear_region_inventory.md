
# (Official) LUA Scripting Documentation

## clear_region_inventory

Clear (remove) an item from all blocks inventories in a cubic region.

___

Spec:

```lua
clear_region_inventory(
	long x1,
	long y1,
	long z1,
	long x2,
	long y2,
	long z2,
	long item_id)
```

## Parameters

- `x1`: The x component of the regions min map point
- `y1`: The y component of the regions min map point
- `z1`: The z component of the regions min map point
- `x2`: The x component of the regions max map point
- `y2`: The y component of the regions max map point
- `z2`: The z component of the regions max map point
- `item_id`: The item to clear. If omitted, all items will be cleared

___

#### Incomplete

This documentation is incomplete

___

### [back](../inventory)
