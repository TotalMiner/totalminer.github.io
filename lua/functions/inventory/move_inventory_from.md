
# (Official) LUA Scripting Documentation

## move_inventory_from

Move (transfer) a blocks inventory to the context actors inventory.

___

Spec:

```lua
move_inventory_from(
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
- `item_id`: The item_id to move. If omitted, all items will be moved
- `qty`: The quantity of the item to move. If omitted, all of the item will be moved

___

#### Incomplete

This documentation is incomplete

___

### [back](../inventory)
