
# (Official) LUA Scripting Documentation

## get_sys_history

Get a value from system history.

___

Spec:

```lua
get_sys_history(
	string key)
```

## Parameters

- `key`: The key/name of the history record

## Returns

- `long`: The history value

___

## Example

```lua
local temp = get_sys_history("temperature")
```

This example gets the value of the system history record with the key "temperature"

___

##### Incomplete

This documentation is incomplete

___

### [back](../history)
