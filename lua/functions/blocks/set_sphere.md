
# (Official) LUA Scripting Documentation

## set_sphere

### Set block id in a spherical region.

Spec:
```lua
set_sphere(
	x,
	y,
	z,
	radius,
	block_id,
	percent,
	seed)
```
## Parameters:
- `x:` The x component of the center of the sphere
- `y:` The y component of the center of the sphere
- `z:` The z component of the center of the sphere
- `radius:` The radius of the sphere (in blocks)
- `block_id:` The block id of the spehere
- `percent:` The percentage of the sphere to fill. Default = 100%
- `seed:` The seed of the prng used when percent is < 100
## Example
```lua
move_region(100,200,300,50,block.basalt,75)
```
This example creates a sphere with a radius of 50 blocks at postion 100,200,300 using basalt as the block id and filling it 75%.
### [back](../blocks)
