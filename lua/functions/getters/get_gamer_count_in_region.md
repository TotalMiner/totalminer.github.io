
# (Official) LUA Scripting Documentation

## get_gamer_count_in_region

Get the total number of enabled gamers currently positioned inside a cubic region.

___

Spec:

```lua
get_gamer_count_in_region(
	long x1,
	long y1,
	long z1,
	long x2,
	long y2,
	long z2)
```

## Parameters

- `x1`: The x component of the regions min world point
- `y1`: The y component of the regions min world point
- `z1`: The z component of the regions min world point
- `x2`: The x component of the regions max world point
- `y2`: The y component of the regions max world point
- `z2`: The z component of the regions max world point

## Returns

- `long`: The number of gamers

___

## Example

```lua
local gamer_count = get_gamer_count_in_region(200,200,200,300,300,300)
```

___

### Incomplete

documentation incomplete

___

### [back](../getters)
