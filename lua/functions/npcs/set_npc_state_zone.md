
# (Official) LUA Scripting Documentation

## set_npc_state_zone

Set the state of all NPCs in a zone.

___

Spec:

```lua
set_npc_state_zone(
	string state,
	string zone,
	bool is_temp_zone,
	string npc_type)
```

## Parameters

- `state`: 
- `zone`: 
- `is_temp_zone`: true or false
- `npc_type`: Only apply to these types of NPCs. Omit to apply to all types of NPCs

___

Valid values for state:
"alive", "dying", "death", "respawning", "respawn", "despawning",
"despawn", "sleeping", "sleep", "custom", "inactive", "delete"

___

##### Incomplete

This documentation is incomplete

___

### [back](../npcs)
