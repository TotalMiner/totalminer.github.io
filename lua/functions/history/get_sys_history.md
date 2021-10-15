
# (Official) LUA Scripting Documentation

## get_sys_history

### Get a value from system history.

Spec:
```lua
get_sys_history(
	key)
```
## Parameters:
- `key:` The key/name of the history record

## Returns:
- `long:` The history value

## Example
```lua
local temp = get_sys_history("temperature")
```
This example gets the value of the system history record with the key "temperature"

### [back](../history)
