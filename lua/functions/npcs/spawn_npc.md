
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

### Loot Table
The loot table specifies either a chest location (map point), or a drop item list (table), or both.
- If no chest location is specified, items are dropped from the drop item list.
- If a chest location is specified and a drop item list, items are dropped from the drop item list only if they are found in the chest.
- If a chest location is specified and no drop item list, a random item from the chest is dropped.

Chance items instruct the game to select a random item.

#### Loot Table Definition:

Point: X, Y, Z: The location of a chest.

Table of DropItems:
- Item: The item to drop. Chance item = select a random item.
- Count: The number of items to drop.
- Percent: The chance of an item dropping. 100 = the item will always drop. 50 = the item will drop half of the time, etc.

### Examples:
```lua
local loot = { point = vec3(1,200,2) } -- loot table is just a chest location
local loot = { item.chance, { item.steelsword, 1, 50 } } -- loot table is a chance item and a steelsword with a 50 percent drop rate.
local loot = { point = vec3(1,200,2), item.chance, { item.steelsword, 1, 50 } } -- loot table is a chest location, chance item and a sword with a 50 percent drop rate.
```
___
### Combat Stats
The combat stats allow you to specify custom health, attack, defence, strength and ranged stats. These 5 stats define the NPCs combat level.

### Examples:
```lua
local stats = { health = 100, attack = 50 } -- health = 100, attack = 50, defence = 1, strength = 1, ranged = 1
local stats = { health = 100, attack = 50, defence = 30, strength = 40, ranged = 10 } -- health = 100, attack = 50, defence = 30, strength = 40, ranged = 10
```


___

## Example

```lua
local name, dialog, kill_script
local x, y, z = get_cursor_point()
local type = "zombie"
local ai = "MyZombieAI"
local stats = { health = 100, attack = 50 }
local chest_pos = vec3(1, 201, 2)
local loot = { point = chest_pos, item.ironsword, item.steelsword, { item.grass, 10, 50 } }
spawn_npc(type, x, y, z, name, ai, dialog, kill_script, stats, loot)
```

This example spawns a Chef NPC at the players cursor, with a custom AI, custom Health and Attack stats, and a custom Loot Table.
            Name is defaulted to "Chef". Dialog and kill_script are empty.
            
            The loot table consists of a chest location of 1,201,2, and three drop items.
            - First drop item is 1 iron sword, 100 percent drop rate.
            - Second item is 1 steel sword, 100 percent drop rate.
            - Third item is 10 grass blocks, 50 percent drop rate.

___

##### Incomplete

This documentation is incomplete

___

### [back](../npcs)
