
# (Official) LUA Scripting Documentation

## get_history

### Get a value from the context players history.
___
Spec:
```lua
get_history(
	key)
```
## Parameters:
- `key:` The key/name of the history record

## Returns:
- `long:` The history value

___
## Examples
```lua
local started = get_history("myquest/started")
```
This example gets the value of the history record with the key "myquest/started"
___
```lua
local temp = get_history("temp")
```
___
### [back](../history)
