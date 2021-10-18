
# (Official) LUA Scripting Documentation

## get_block_info

Get various world data of a block.

___

Spec:

```lua
get_block_info(
	long x,
	long y,
	long z)
```

## Parameters

- `x`: The x component of the map point of the block.
- `y`: The y component of the map point of the block.
- `z`: The z component of the map point of the block.

## Returns

- `block_info`: A data type containing fields for the block state
- `bool`: is_edited. True if the block has been edited (is not naturally generated)
- `bool`: is_light_source. True if the block emits light
- `bool`: is_open. True if the blocks interface screen is open
- `bool`: is_ore. True if the block is a naturally generated ore
- `bool`: is_passable. True if actors can pass through the block
- `bool`: is_delivering_power. True if the block is currently delivering power (to surrounding blocks)
- `bool`: is_receiving_power. True if the block is currently receiving power
- `bool`: is_solid. True if the block has solid geometry (no gaps to see though)
- `long`: tex_id. The current texture id (for blocks who's texture can be reassigned)
- `long`: resistance. The blocks resistance to mining

___

#### Incomplete

This documentation is incomplete

___

### [back](../getters)
