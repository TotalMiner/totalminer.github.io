
# (Official) LUA Scripting Documentation

## add_block_inventory

Add or subtract a quantity of an item to/from a blocks inventory.

___

Spec:

```lua
add_block_inventory(
	x,
	y,
	z,
	item_id,
	qty)
```

## Parameters

- `x`: The x component of the position of the block.
- `y`: The y component of the position of the block.
- `z`: The z component of the position of the block.
- `item_id`: 
- `qty`: The quantity to add. If ommitted, 1 item will be added. Use a negative number to remove items from inventory

___

### [back](../inventory)
