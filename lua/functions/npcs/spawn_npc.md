
# (Official) LUA Scripting Documentation

## spawn_npc

Spawn an NPC (Non Player Character).

___

Spec:

```lua
spawn_npc(
	string type,
	long x,
	long y,
	long z,
	string name,
	string ai,
	string dialog,
	string kill_script,
	NLua.LuaTable combat_stats,
	NLua.LuaTable loot_table)
```

## Parameters

- `type`: The type of the NPC
- `x`: The x component of the map point to spawn the NPC
- `y`: The y component of the map point to spawn the NPC
- `z`: The z component of the map point to spawn the NPC
- `name`: The name of the NPC
- `ai`: The name of the ai behaviour tree for the NPC
- `dialog`: The name of the dialog tree for the NPC
- `kill_script`: The name of the script to execute if/when the NPC is killed
- `combat_stats`: Stats to define the NPCs combat level
- `loot_table`: A Loot Table that defines what an NPC can drop when killed. loot_table is currently not supported

___

## Example

```lua
local x, y, z = get_cursor_point()
local type = "chef"
local name, dialog, kill_script
local ai = "MyChefAI"
local stats = { health = 100, attack = 25 }
spawn_npc(type, x, y, z, name, ai, dialog, kill_script, stats)
```

This example spawns a Chef NPC at the players cursor, with a custom AI and custom Health+Attack stat. Name is defaulted to "Chef". Dialog and kill_script are empty.

___

##### Incomplete

This documentation is incomplete

___

### [back](../npcs)
