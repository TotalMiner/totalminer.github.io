
# (Official) LUA Scripting Documentation

## get_cursor_point

Get the world point of the context actor block cursor.

___

Spec:

```lua
get_cursor_point()
```

## Returns

- `long`: The x component of the cursor point
- `long`: The y component of the cursor point
- `long`: The z component of the cursor point

___

if y == 0 then the cursor is invalid (not targeting a block)

___

## Example

```lua
local x,y,z = get_cursor_point()
set_block(x,y,z,block.clay)
```

This example sets the block currently highlighted by the players cursor to clay

___

##### Incomplete

This documentation is incomplete

___

### [back](../getters)
