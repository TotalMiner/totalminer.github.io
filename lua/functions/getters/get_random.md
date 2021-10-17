
# (Official) LUA Scripting Documentation

## get_random

Get a random number.

___

Spec:

```lua
get_random(
	long max)
```

## Parameters

- `max`: The highest number

## Returns

- `long`: The random number

___

The number generated will be between 0 and `max` inclusive

___

## Example

```lua
notify("The dice roll equals ", get_random(5)+1)
```

___

### Incomplete

This documentation is incomplete

___

### [back](../getters)
