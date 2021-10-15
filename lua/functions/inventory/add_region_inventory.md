
# (Official) LUA Scripting Documentation

## add_region_inventory

### Add or subtract a quantity of an item to/from all block inventories in a cubic region.

Spec:
```lua
add_region_inventory(
	x1,
	y1,
	z1,
	x2,
	y2,
	z2,
	item_id,
	qty)
```
## Parameters:
- `x1:` The x component of the regions min position
- `y1:` The y component of the regions min position
- `z1:` The z component of the regions min position
- `x2:` The x component of the regions max position
- `y2:` The y component of the regions max position
- `z2:` The z component of the regions max position
- `item_id:` 
- `qty:` The quantity to add. If ommitted, 1 item will be added. Use a negative number to remove items from inventory
### [back](../inventory)
