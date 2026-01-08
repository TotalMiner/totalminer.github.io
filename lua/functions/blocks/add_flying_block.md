
# (Official) LUA Scripting Documentation

## add_flying_block

Add a falling block at the map point.

___

Spec:

```lua
add_flying_block(
	long x,
	long y,
	long z,
	long block_id,
	double vel_x,
	double vel_y,
	double vel_z,
	double gravity,
	double break_chance)
```

## Parameters

- `x`: The x component of the map point
- `y`: The y component of the map point
- `z`: The z component of the map point
- `block_id`: The block id
- `vel_x`: The x velocity of the block
- `vel_y`: The y velocity of the block
- `vel_z`: The z velocity of the block
- `gravity`: A gravity multiplier
- `break_chance`: The chance the block will break on impact. This is a decimal between 0 and 1, 0 being 0% and 1 being 100%.

___

## Example

```lua
add_flying_block(0, 230, 0, block.dirt, 0, 0, 0, 1, 0.5)
```

Spawns a flying dirt block at 0, 230, 0 that will fall straight down with a gravity muliplier of 1.

___

##### Incomplete

This documentation is incomplete

___

### [back](../blocks)
