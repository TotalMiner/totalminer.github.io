
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

## Examples

```lua
equip(item.woodsword,"right")
```

___

```lua
equip(item.leatherhelmet,"body")
```

___

### Incomplete

This documentation is incomplete

___

### [back](../other)
