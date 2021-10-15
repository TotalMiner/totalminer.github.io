
# (Official) LUA Scripting Documentation

## clear_block_inventory

### Clear (remove) an item from a blocks inventory.

Spec:
```lua
clear_block_inventory(
	x,
	y,
	z,
	item_id)
```
## Parameters:
- `x:` The x component of the position of the block.
- `y:` The y component of the position of the block.
- `z:` The z component of the position of the block.
- `item_id:` The item to clear. If omitted, all items will be cleared

### [back](../inventory)
