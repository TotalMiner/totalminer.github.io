
# (Official) LUA Scripting Documentation

## get_cursor_face

Get the face of the block targeted by the context actor block cursor.

___

Spec:

```lua
get_cursor_face()
```

## Returns

- `long`: The block face

___

A return value of zero means the cursor is invalid (not targeting a block)
- 0 = No face (cursor is invalid)
- 1 = Left/West
- 2 = Forward/North
- 3 = Right/East
- 4 = Backward/South
- 5 = Up
- 6 = Down

___

## Example

```lua
local face = get_cursor_face()
```

___

##### Incomplete

This documentation is incomplete

___

### [back](../getters)
