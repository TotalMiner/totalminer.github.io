
# (Official) LUA Scripting Documentation

## add_pickup

Spawn a pickup item.

___

Spec:

```lua
add_pickup(
	double x,
	double y,
	double z,
	long item_id,
	long qty)
```

## Parameters

- `x`: The x component of the world position to spawn the pickup.
- `y`: The y component of the world position to spawn the pickup.
- `z`: The z component of the world position to spawn the pickup.
- `item_id`: The item of the pickup.
- `qty`: The qty of units gained if the pickup is picked up

___

## Example

```lua
add_pickup(100,220,140,item.wood,2)
```

___

#### Incomplete

This documentation is incomplete

___

### [back](../other)
