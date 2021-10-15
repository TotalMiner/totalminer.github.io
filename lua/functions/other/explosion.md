
# (Official) LUA Scripting Documentation

## explosion

### Create an explosion.
___
Spec:
```lua
explosion(
	x,
	y,
	z,
	radius,
	strength)
```
## Parameters:
- `x:` The x component of the position of the explosion.
- `y:` The y component of the position of the explosion.
- `z:` The z component of the position of the explosion.
- `radius:` The radius of the explosion specified in blocks
- `strength:` The strength of the explosion (some blocks are resistant to low strength explosions

___
Players and NPCs in the vicinity of the explosions can also be damaged

___
## Example
```lua
explosion(100,200,300,30,5)
```
___
### [back](../other)
