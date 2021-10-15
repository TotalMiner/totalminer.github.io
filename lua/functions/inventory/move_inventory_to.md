
# (Official) LUA Scripting Documentation

## move_inventory_to

### Move (transfer) the context actors inventory to a block's inventory.
___
Spec:
```lua
move_inventory_to(
	x,
	y,
	z,
	item_id,
	qty)
```
## Parameters:
- `x:` The x component of the position of the block.
- `y:` The y component of the position of the block.
- `z:` The z component of the position of the block.
- `item_id:` The item_id to move. If omitted, all items will be moved
- `qty:` The quantity of the item to move. If omitted, all of the item will be moved

___
### [back](../inventory)
