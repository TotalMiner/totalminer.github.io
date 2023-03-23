
# (Official) LUA Scripting Documentation

## equip

Cause the context actor to equip an item.

___

Spec:

```lua
equip(
	long item_id,
	string slot)
```

## Parameters

- `item_id`: The item to equip
- `slot`: The slot to equip to: left, right or body

___

Valid values for slot: "left", "right", "body"

___

## Examples

```lua
equip(item.woodsword,"right")
```

This example equips a wood sword (if the actor has one) to their right hand

___

```lua
equip(item.leatherhelmet,"body")
```

This example equips a leather helmet (if the actor has one) to the appropriate body slot

___

##### Incomplete

This documentation is incomplete

___

### [back](../other)
