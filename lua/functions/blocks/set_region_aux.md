
# (Official) LUA Scripting Documentation

## set_region_aux

### Set aux data in a cubic region.
___
Spec:
```lua
set_region_aux(
	x1,
	y1,
	z1,
	x2,
	y2,
	z2,
	_aux,
	high,
	percent,
	seed)
```
## Parameters:
- `x1:` The x component of the regions min position
- `y1:` The y component of the regions min position
- `z1:` The z component of the regions min position
- `x2:` The x component of the regions max position
- `y2:` The y component of the regions max position
- `z2:` The z component of the regions max position
- `_aux:` 
- `high:` 
- `percent:` The percentage of the region to set. Default = 100%
- `seed:` The seed of the prng used when percent is < 100

___
### [back](../blocks)
