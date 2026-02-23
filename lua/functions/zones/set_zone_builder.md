
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

- `name`: The name of the zone to set the builder of.
- `builder_type`: The zone builder to add or clear.

___

Valid builder_types are:
- "Player" - Sets the zone builder to the player running the script.
- "Clan" - Sets the zone builder to the clan of the player running the script.
- "None" - Removes the builder from the zone.


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
