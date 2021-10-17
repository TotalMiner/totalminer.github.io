
# (Official) LUA Scripting Documentation

## get_hour

Get the current game hour from the 24 hour day clock.

___

Spec:

```lua
get_hour()
```

## Returns

- `double`: The current hour. 0 = 12am (midnight). 8.5 = 8:30am. 12 = 12pm (midday). 23 = 11pm.

___

## Example

```lua
local time = get_hour()
if time > 16 then notify("Evening is approaching") end
```

___

### Incomplete

This documentation is incomplete

___

### [back](../getters)
