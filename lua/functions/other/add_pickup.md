
# (Official) LUA Scripting Documentation

## add_pickup
#
### Spawn a pickup item.
#
Spec:
```lua
add_pickup(
	x,
	y,
	z,
	item_id,
	qty)
```
#
## Parameters:
- `x:` The x component of the position to spawn the pickup.
- `y:` The y component of the position to spawn the pickup.
- `z:` The z component of the position to spawn the pickup.
- `item_id:` The item of the pickup.
- `qty:` The qty of units gained if the pickup is picked up
#  

## Example
```lua
add_pickup(100,220,140,item.wood,2)
```
#
### [back](../other)
