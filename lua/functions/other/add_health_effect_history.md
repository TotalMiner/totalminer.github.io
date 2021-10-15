
# (Official) LUA Scripting Documentation

## add_health_effect_history

### Add an effect which increases or decreases the context actor's health over time.

Spec:
```lua
add_health_effect_history(
	points,
	history_key,
	millisecs,
	name)
```
## Parameters:
- `points:` The number of hitpoints per effect. A positive number increases health, a negative number decreases health
- `history_key:` The effect is only applied if this history record exists
- `millisecs:` The time in milliseconds between each effect
- `name:` 
## Example
```lua
add_health_effect(2,"poison",3000)
```
This example increases the actors health by 2 hitpoints every 3 seconds as long as `get_history("poison") ~= 0`
### [back](../other)
