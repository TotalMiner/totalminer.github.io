
# (Official) LUA Scripting Documentation

## set_region_aux

Set aux data in a cubic region.

___

Spec:

```lua
set_region_aux(
	long x1,
	long y1,
	long z1,
	long x2,
	long y2,
	long z2,
	long _aux,
	bool high,
	long percent,
	long seed)
```

## Parameters

- `x1`: The x component of the regions min map point
- `y1`: The y component of the regions min map point
- `z1`: The z component of the regions min map point
- `x2`: The x component of the regions max map point
- `y2`: The y component of the regions max map point
- `z2`: The z component of the regions max map point
- `_aux`: 
- `high`: 
- `percent`: The percentage of the region to set. Default = 100%
- `seed`: The seed of the prng used when percent is < 100

___

##### Incomplete

This documentation is incomplete

___

### [back](../blocks)
