
# (Official) LUA Scripting Documentation

## replace_region

Replace a block id with another block id in a cubic region.

___

Spec:

```lua
replace_region(
	long x1,
	long y1,
	long z1,
	long x2,
	long y2,
	long z2,
	long block_id1,
	long block_id2,
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
- `block_id1`: The block id to replace
- `block_id2`: The block id to replace with (the new block id)
- `percent`: The percentage of the region to replace. Default = 100%
- `seed`: The seed of the prng used when percent is < 100

___

### Incomplete

This documentation is incomplete

___

### [back](../blocks)
