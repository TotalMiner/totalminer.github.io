
# (Official) LUA Scripting Documentation

## replace_region

### Replace a block id with another block id in a cubic region.

Spec:
```lua
replace_region(
	x1,
	y1,
	z1,
	x2,
	y2,
	z2,
	block_id1,
	block_id2,
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
- `block_id1:` The block id to replace
- `block_id2:` The block id to replace with (the new block id)
- `percent:` The percentage of the region to replace. Default = 100%
- `seed:` The seed of the prng used when percent is < 100
### [back](../blocks)
