
# (Official) LUA Scripting Documentation

## set_temp_zone_types

Set a temp zone's types.

___

Spec:

```lua
set_temp_zone_types(
	string name,
	bool spawn,
	bool no_edit,
	bool no_combat,
	bool no_fly,
	bool no_mobs,
	bool no_escape)
```

## Parameters

- `name`: 
- `spawn`: true or false. If true, a player will spawn to a random location within this zone. If more than one spawn zone exists, the player will pick a spawn zone randomly to spawn into. Spawn zones must be at least 2 x 2 x 2 blocks in size and must not have any blocks inside them (they must be empty space). Spawn zones are not editable by default
- `no_edit`: true or false. If true, players cannot add or remove blocks from inside the zone
- `no_combat`: true or false. If true, players cannot engage in combat while inside the zone
- `no_fly`: true or false. If true, players cannot fly inside the zone
- `no_mobs`: true or false. If true, mobs cannot spawn inside the zone
- `no_escape`: true or false. If true, players cannot use the Escape option inside the zone

___


- If more than one spawn zone exists, the player will pick a spawn zone randomly to spawn into.
- Spawn zones must be at least 2 x 2 x 2 blocks in size and must not have any blocks inside them (they must be empty space).
- Spawn zones are not editable by default.


___

##### Incomplete

This documentation is incomplete

___

### [back](../zones)
