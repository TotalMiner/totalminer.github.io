
# (Official) LUA Scripting Documentation

## get_item

Get an equipped or event raising item.

___

Spec:

```lua
get_item(
	string src)
```

## Parameters

- `src`: The item source. Omit to get the item that caused the script to be executed (via ItemSwing event)

## Returns

- `long`: The item id. omit to use current itemID

___

Valid values for source are:
"left", "right", "head", "neck", "body", "legs", "feet", "leftside", "rightside"

___

##### Incomplete

This documentation is incomplete

___

### [back](../getters)
