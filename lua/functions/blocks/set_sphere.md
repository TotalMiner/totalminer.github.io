
# (Official) LUA Scripting Documentation

## set_sphere

Set block id in a spherical region.

___

Spec:

```lua
set_sphere(
	long x,
	long y,
	long z,
	long radius,
	long block_id,
	long percent,
	long seed)
```

## Parameters

- `x`: The x component of the map point at the center of the sphere
- `y`: The y component of the map point at the center of the sphere
- `z`: The z component of the map point at the center of the sphere
- `radius`: The radius of the sphere (in blocks)
- `block_id`: The block id of the spehere
- `percent`: The percentage of the sphere to fill. Default = 100%
- `seed`: The seed of the prng used when percent is < 100

___

## Example

```lua
move_region(100,200,300,50,block.basalt,75)
```

This example creates a sphere with a radius of 50 blocks at postion 100,200,300 using basalt as the block id and filling it 75%.

___

#### Incomplete

This documentation is incomplete

___

### [back](../blocks)
