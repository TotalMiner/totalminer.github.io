
# (Official) LUA Scripting Documentation

## set_block

Set block id and aux data at a map point.

___

Spec:

```lua
set_block(
	long x,
	long y,
	long z,
	long block_id,
	long aux)
```

## Parameters

- `x`: The x component of the map point
- `y`: The y component of the map point
- `z`: The z component of the map point
- `block_id`: The numerical block value, this can also be from the global block enum
- `aux`: The auxiliary data for setting orientation (This can be omitted)

___

## Examples

```lua
set_block(100, 201, 100, block.grass)
```

Sets a grass block at 100, 201, 100.

___

```lua
set_block (100, 201, 100, block.stairs, 14)
```

Sets a stairs block at 100, 201, 100 that is upside down and facing east.

___

##### Incomplete

This documentation is incomplete

___

### [back](../blocks)
