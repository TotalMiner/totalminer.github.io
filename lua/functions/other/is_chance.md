
# (Official) LUA Scripting Documentation

## is_chance

A dice query (same as is_random).

___

Spec:

```lua
is_chance(
	long chance,
	long chances)
```

## Parameters

- `chance`: Numbers for a win
- `chances`: Number of sides on the dice

## Returns

- `bool`: True if the dice throw was won

___

## Examples

```lua
is_chance(1,6)
```

A classic 6 sided dice throw. Won if 1 is thrown

___

```lua
is_chance(2,20)
```

Won if 1 or 2 is thrown on an 20 sided dice (10% chance)

___

### Incomplete

This documentation is incomplete

___

### [back](../other)
