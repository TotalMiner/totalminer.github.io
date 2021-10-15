
# (Official) LUA Scripting Documentation

## clear_region_inventory
#
### Clear (remove) an item from all blocks inventories in a cubic region.
#
Spec:
```lua
clear_region_inventory(
	x1,
	y1,
	z1,
	x2,
	y2,
	z2,
	item_id)
```
#
## Parameters:
- `x1:` The x component of the regions min position
- `y1:` The y component of the regions min position
- `z1:` The z component of the regions min position
- `x2:` The x component of the regions max position
- `y2:` The y component of the regions max position
- `z2:` The z component of the regions max position
- `item_id:` The item to clear. If omitted, all items will be cleared
#  

### [back](../inventory)
