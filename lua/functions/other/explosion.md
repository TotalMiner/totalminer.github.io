
# (Official) LUA Scripting Documentation

## explosion

Create an explosion.

___

Spec:

```lua
explosion(
	long x,
	long y,
	long z,
	long radius,
	long strength)
```

## Parameters

- `x`: The x component of the map point of the explosion.
- `y`: The y component of the map point of the explosion.
- `z`: The z component of the map point of the explosion.
- `radius`: The radius of the explosion specified in blocks
- `strength`: The strength of the explosion (some blocks are resistant to low strength explosions

___

Players and NPCs in the vicinity of the explosions can also be damaged

___

## Example

```lua
explosion(100,200,300,30,5)
```

___

#### Incomplete

This documentation is incomplete

___

### [back](../other)
