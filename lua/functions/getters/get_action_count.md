
# (Official) LUA Scripting Documentation

## get_action_count

Get the number of actions the context actor has performed.

___

Spec:

```lua
get_action_count(
	string action,
	long item_id)
```

## Parameters

- `action`: The type of action
- `item_id`: The item associated with the action

## Returns

- `long`: The number of actions

___

The possible action types are:
- "used" => How many times the actor has used the item
- "crafted" => How many times the actor has crafted the item
- "collected" => How many times the actor has collected the item (via pickups)
- "mined" => How many times the actor has mined the item (blocks only)


___

## Example

```lua
notify("Player has mined ", get_action_count("mined",block.clay), " blocks of clay")
```

___

##### Incomplete

This documentation is incomplete

___

### [back](../getters)
