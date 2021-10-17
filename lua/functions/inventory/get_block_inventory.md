
# (Official) LUA Scripting Documentation

## get_block_inventory

Get the total count of an item in a block's inventory.

___

Spec:

```lua
get_block_inventory(
	long x,
	long y,
	long z,
	long item_id)
```

## Parameters

- `x`: The x component of the map point of the block.
- `y`: The y component of the map point of the block.
- `z`: The z component of the map point of the block.
- `item_id`: The item to count. If item_id is ommitted or is item.none then the result is the total of all items in inventory

## Returns

- `long`: The total number of item_id's in the block's inventory

___

### Incomplete

This documentation is incomplete

___

### [back](../inventory)
