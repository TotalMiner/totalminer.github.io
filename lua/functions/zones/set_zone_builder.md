
# (Official) LUA Scripting Documentation

## set_zone_builder

Adds or clears zone builders.

___

Spec:

```lua
set_zone_builder(
	string name,
	string builder_type)
```

## Parameters

- `name`: Target Zone Name
- `builder_type`: Can be passed player,clan,none if player is passed will set builder to players name running script

___

## Examples

```lua
set_zone_builder("Player Building Area", "player")
```

Sets the zone "Player Building Area" builder to the context player.

___

```lua
set_zone_builder("Clan Town", "clan")
```

Sets the zone "Clan Town" to the context player's clan.

___

##### Incomplete

This documentation is incomplete

___

### [back](../zones)
