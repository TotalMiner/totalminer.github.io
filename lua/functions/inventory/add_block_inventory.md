
# (Official) LUA Scripting Documentation

## add_block_inventory

Add or subtract a quantity of an item to/from a blocks inventory.

___

Spec:

```lua
add_block_inventory(
	long x,
	long y,
	long z,
	long item_id,
	long qty)
```

## Parameters

- `x`: The x component of the map point of the block.
- `y`: The y component of the map point of the block.
- `z`: The z component of the map point of the block.
- `item_id`: 
- `qty`: The quantity to add. If ommitted, 1 item will be added. Use a negative number to remove items from inventory

___

##### Incomplete

This documentation is incomplete

___

### [back](../inventory)
