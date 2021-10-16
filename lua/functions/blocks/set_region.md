
# (Official) LUA Scripting Documentation

## set_region

Set block id in a cubic region.

___

Spec:

```lua
set_region(
	x1,
	y1,
	z1,
	x2,
	y2,
	z2,
	block_id,
	percent,
	seed)
```

## Parameters

- `x1`: The x component of the regions min position
- `y1`: The y component of the regions min position
- `z1`: The z component of the regions min position
- `x2`: The x component of the regions max position
- `y2`: The y component of the regions max position
- `z2`: The z component of the regions max position
- `block_id`: 
- `percent`: The percentage of the region to set. Default = 100%
- `seed`: The seed of the prng used when percent is < 100

___

### [back](../blocks)
