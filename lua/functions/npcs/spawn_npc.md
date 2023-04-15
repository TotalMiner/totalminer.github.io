
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
- `loot_table`: A Loot Table that defines what an NPC can drop when killed

___

The loot table specifies either a chest location, or a drop item list, or both.
- If no chest location is specified, items are dropped from the drop item list.
- If a chest location is specified and a drop item list, items are dropped from the drop item list only if they are found in the chest.
- If a chest location is specified and no drop item list, a random item from the chest is dropped.
Chance items instruct the game to select a random item.
Loot Table:
Point: X, Y, Z: The location of a chest.
Table of DropItems:
- Item: The item to drop. Chance item = select a random item.
- Count: The number of items to drop.
- Percent: The chance of an item dropping. 100 = the item will always drop. 50 = the item will drop half of the time, etc.


___

## Example

```lua
local name, dialog, kill_script
local x, y, z = get_cursor_point()
local type = "zombie"
local ai = "MyZombieAI"
local stats = { health = 100, attack = 50 }
local chest_pos = vector3(1, 201, 2)
local loot = { point = chest_pos, item.ironsword, item.steelsword, { item.grass, 10, 50 } }
spawn_npc(type, x, y, z, name, ai, dialog, kill_script, stats, loot)
```

This example spawns a Chef NPC at the players cursor, with a custom AI, custom Health and Attack stats, and a custom Loot Table. Name is defaulted to "Chef". Dialog and kill_script are empty.

___

##### Incomplete

This documentation is incomplete

___

### [back](../npcs)
