
# (Official) LUA Scripting Documentation

## get_actor_id

Get the unique id of the context actor.

___

Spec:

```lua
get_actor_id()
```

## Returns

- `string`: Returns the actor's unique id. If the actor is an NPC the return value will be 0.

___

## Example

```lua
notify("Your ID is: "..get_actor_id())
```

___

##### Incomplete

This documentation is incomplete

___

### [back](../getters)
