
# (Official) LUA Scripting Documentation

## set_texture

Set a block's visible texture.

___

Spec:

```lua
set_texture(
	long x,
	long y,
	long z,
	long tex_id)
```

## Parameters

- `x`: The x component of the map point of the block.
- `y`: The y component of the map point of the block.
- `z`: The z component of the map point of the block.
- `tex_id`: The numerical value of active texture list starting at 0.

___

## Example

```lua
set_texture(73, 201, 85, 3)
```

Sets the texture of the block at 73, 201, 85 to the fourth active texture for that block.

___

##### Incomplete

This documentation is incomplete

___

### [back](../other)
