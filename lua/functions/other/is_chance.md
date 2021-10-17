
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

___

```lua
is_chance(2,20)
```

___

#### Incomplete

This documentation is incomplete

___

### [back](../other)
