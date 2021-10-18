
# (Official) LUA Scripting Documentation

## set_zone_props

Set a zone's properties.

___

Spec:

```lua
set_zone_props(
	string name,
	long combat_diff,
	long jump_count,
	double speed_multiplier,
	double gravity_multiplier,
	double health_multiplier)
```

## Parameters

- `name`: 
- `combat_diff`: The combat level difference for the zone. Combat cannot be engaged by players or mobs if the difference between their combat levels is greater than this number
- `jump_count`: The number of times a player can jump while still in the air. The default is two.
- `speed_multiplier`: This number is multiplied by the players base speed to calculate the players final speed. Default is one
- `gravity_multiplier`: This number is multiplied by the players base gravity to calculate the players final gravity. Default is one
- `health_multiplier`: This number is multiplied by the players base health regeneration speed to calculate the players final health regeneration speed. Default is one

___

##### Incomplete

This documentation is incomplete

___

### [back](../zones)
