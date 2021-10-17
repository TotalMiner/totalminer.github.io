
# (Official) LUA Scripting Documentation

## add_health_effect

Add an effect which increases or decreases the context actor's health over time.

___

Spec:

```lua
add_health_effect(
	long points,
	long millisecs,
	long duration,
	string name)
```

## Parameters

- `points`: The number of hitpoints per effect. A positive number increases health, a negative number decreases health
- `millisecs`: The time in milliseconds between each effect
- `duration`: The time in milliseconds for the effect to last
- `name`: 

___

If duration and millisecs are omitted, the effect is applied only once

___

## Examples

```lua
add_health_effect(2,3000,4000)
```

___

```lua
add_health_effect(-5)
```

___

### Incomplete

This documentation is incomplete

___

### [back](../other)
