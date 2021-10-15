
# (Official) LUA Scripting Documentation

## equip

### Cause the context actor to equip an item.

Spec:
```lua
equip(
	item_id,
	slot)
```
## Parameters:
- `item_id:` The item to equip
- `slot:` The slot to equip to: left, right or body

## Examples
```lua
equip(item.woodsword,"right")
```
This example equips a wood sword (if the actor has one) to their right hand
```lua
equip(item.leatherhelmet,"body")
```
This example equips a leather helmet (if the actor has one) to the appropriate body slot

### [back](../other)
