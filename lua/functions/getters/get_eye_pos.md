
# (Official) LUA Scripting Documentation

## get_eye_pos

Get the current world eye position of the context actor (camera position).

___

Spec:

```lua
get_eye_pos()
```

## Returns

- `double`: The x component of the position
- `double`: The y component of the position
- `double`: The z component of the position

___

The world position components are world space coordinates so they are floating point numbers. The position is the actors eye position. If the actor is a player, then this is equivalent to the players camera position

___

##### Incomplete

This documentation is incomplete

___

### [back](../getters)
