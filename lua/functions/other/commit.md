
# (Official) LUA Scripting Documentation

## commit

### Force a chunk mesh update.
___
Spec:
```lua
commit()
```

___
Chunk meshes define the graphics (triangles, textures and lighting) of the voxel blocks in the world.
When a block is added or removed from the world, the mesh must be updated to visually show that change.
Mesh updating is a relatively expensive operation so the game does not automatically update the mesh everytime
a script command changes voxel data (block, aux or light).  If a script changed a bunch of blocks and the game
automatically updated the mesh after every change, some latency/lagginess would appear with the mesh updates.
So instead, the game requires you to issue a commit command to tell it you now want it to update the mesh.
A commit command is only required if you want to update the mesh while the script is still executing.
By default, if a script changes voxel data, the mesh is automatically updated when a script ends execution,
so you don't need to issue the command in every script that edits voxel data, as mentioned above,
you only need to use this command if you want the mesh updated before the script ends.

___
### [back](../other)
