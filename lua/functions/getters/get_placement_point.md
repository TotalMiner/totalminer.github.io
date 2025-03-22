
# (Official) LUA Scripting Documentation

## get_placement_point

Get the world point where a block would be placed by the context actor.

___

Spec:

```lua
get_placement_point()
```

## Returns

- `long`: The x component of the placement point
- `long`: The y component of the placement point
- `long`: The z component of the placement point

___

if y == 0 then the cursor / placement point is invalid (not targeting a block)

___

## Example

```lua
local x,y,z = get_placement_point()
set_block(x,y,z,block.clay)
```

___

##### Incomplete

This documentation is incomplete

___

### [back](../getters)
