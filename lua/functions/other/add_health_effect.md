
# (Official) LUA Scripting Documentation

## add_health_effect

### Add an effect which increases or decreases the context actor's health over time.
___
Spec:
```lua
add_health_effect(
	points,
	millisecs,
	duration,
	name)
```
## Parameters:
- `points:` The number of hitpoints per effect. A positive number increases health, a negative number decreases health
- `millisecs:` The time in milliseconds between each effect
- `duration:` The time in milliseconds for the effect to last
- `name:` 

___
If duration and millisecs are omitted, the effect is applied only once

___
## Examples
```lua
add_health_effect(2,3000,4000)
```
This example increases the actors health by 2 hitpoints every 3 seconds over a time period of 4 seconds

___
```lua
add_health_effect(-5)
```
This example decreases the actors health by 5 hitpoints (once only)

___
### [back](../other)
