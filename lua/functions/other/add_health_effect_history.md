
# (Official) LUA Scripting Documentation

## add_health_effect_history

Add an effect which increases or decreases the context actor's health over time.

___

Spec:

```lua
add_health_effect_history(
	long points,
	string history_key,
	long millisecs,
	string name)
```

## Parameters

- `points`: The number of hitpoints per effect. A positive number increases health, a negative number decreases health
- `history_key`: The effect is only applied if this history record exists
- `millisecs`: The time in milliseconds between each effect
- `name`: 

___

## Example

```lua
add_health_effect_history(2,"poison",3000)
```

___

### Incomplete

This documentation is incomplete

___

### [back](../other)
