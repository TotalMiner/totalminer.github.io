
# (Official) LUA Scripting Documentation

## get_clan_history

### Get a value from the context player's clan history.
___
Spec:
```lua
get_clan_history(
	key)
```
## Parameters:
- `key:` The key/name of the history record

## Returns:
- `long:` The history value

___
## Example
```lua
local member_count = get_clan_history("member count")
```
This example gets the value of the clan history record with the key "member count"
___
### [back](../history)
