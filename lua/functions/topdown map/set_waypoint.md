
# (Official) LUA Scripting Documentation

## set_waypoint

Set a waypoint for the context player.

___

Spec:

```lua
set_waypoint(
	long x,
	long z)
```

## Parameters

- `x`: The x component of the map point
- `z`: The z component of the map point

___

## Example

```lua
set_waypoint(150, 75)
```

Sets the player's waypoint to 150, 75. No Y is needed due to waypoints not having a height value.

___

##### Incomplete

This documentation is incomplete

___

### [back](../topdown map)
