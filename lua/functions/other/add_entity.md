
# (Official) LUA Scripting Documentation

## add_entity

Add (spawn) a single entity.

___

Spec:

```lua
add_entity(
	double x,
	double y,
	double z,
	double duration,
	double velocity_x,
	double velocity_y,
	double velocity_z,
	double scale,
	string com_pack,
	string com_name,
	bool is_face_forward,
	bool is_collidable,
	double draw_pos_offset_x,
	double draw_pos_offset_y,
	double draw_pos_offset_z,
	double draw_rot_offset_y)
```

## Parameters

- `x`: The x component of the world position of the entity
- `y`: The y component of the world position of the entity
- `z`: The z component of the world position of the entity
- `duration`: The duration (lifetime) of the entity in seconds.
- `velocity_x`: The x component of the velocity of the entity
- `velocity_y`: The y component of the velocity of the entity
- `velocity_z`: The z component of the velocity of the entity
- `scale`: The relative size of the entity blocks. 1 = normal world block size
- `com_pack`: The name of the component pack
- `com_name`: The name of the component
- `is_face_forward`: The entity will face the direction of it's movement (velocity)
- `is_collidable`: The entity will collide with actors (Players and NPCs)
- `draw_pos_offset_x`: Draw position offset
- `draw_pos_offset_y`: Draw position offset
- `draw_pos_offset_z`: Draw position offset
- `draw_rot_offset_y`: Draw rotation offset for the Y axis

___

Entities will be removed if they move outside the game world

___

##### Incomplete

This documentation is incomplete

___

### [back](../other)
