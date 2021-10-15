
# (Official) LUA Scripting Documentation

## spawn_npc

### Spawn an NPC (Non Player Character).

Spec:
```lua
spawn_npc(
	type,
	x,
	y,
	z,
	name,
	ai,
	dialog,
	kill_script)
```
## Parameters:
- `type:` The type of the NPC
- `x:` The x component of the position to spawn the NPC.
- `y:` The y component of the position to spawn the NPC.
- `z:` The z component of the position to spawn the NPC.
- `name:` The name of the NPC
- `ai:` The name of the ai behaviour tree for the NPC
- `dialog:` The name of the dialog tree for the NPC
- `kill_script:` The name of the script to execute if/when the NPC is killed
### [back](../npcs)
