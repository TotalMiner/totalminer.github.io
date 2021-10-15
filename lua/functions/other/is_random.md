
# (Official) LUA Scripting Documentation

## is_random

### A dice query (same as is_chance).

Spec:
```lua
is_random(
	chance,
	chances)
```
## Parameters:
- `chance:` Numbers for a win
- `chances:` Number of sides on the dice
## Returns:
- `bool:` True if the dice throw was won
## Examples
```lua
is_chance(1,6)
```
A classic 6 sided dice throw. Won if 1 is thrown
```lua
is_chance(2,20)
```
Won if 1 or 2 is thrown on an 20 sided dice (10% chance)
### [back](../other)
