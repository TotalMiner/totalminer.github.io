
# (Official) LUA Scripting Documentation

## get_cursor_point

Get the world point of the players block cursor.

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

## Example

```lua
local x,y,z = get_cursor_point()
set_block(x,y,z,block.clay)
```

___

### Incomplete

This documentation is incomplete

___

### [back](../getters)
