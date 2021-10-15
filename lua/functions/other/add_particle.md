
# (Official) LUA Scripting Documentation

## add_particle

Add (emit) a single particle.

___

Spec:

```lua
add_particle(
	x,
	y,
	z,
	duration,
	velocity_x,
	velocity_y,
	velocity_z,
	size_x,
	size_y,
	size_z,
	size_end,
	start_color_r,
	start_color_g,
	start_color_b,
	start_color_a,
	gravity,
	rotation,
	velocity_var_x,
	velocity_var_y,
	velocity_var_z,
	end_color_r,
	end_color_g,
	end_color_b,
	end_color_a,
	emit_pos_var_x,
	emit_pos_var_y,
	emit_pos_var_z,
	emit_pos_offset_x,
	emit_pos_offset_y,
	emit_pos_offset_z)
```

## Parameters

- `x:` The x component of the base start position of the particle
- `y:` The y component of the base start position of the particle
- `z:` The z component of the base start position of the particle
- `duration:` The duration (lifetime) of the particle in seconds.
- `velocity_x:` The x component of the base start velocity of the particle
- `velocity_y:` The y component of the base start velocity of the particle
- `velocity_z:` The z component of the base start velocity of the particle
- `size_x:` The x component of the start size of the particle (width)
- `size_y:` The y component of the start size of the particle (height)
- `size_z:` The z component of the start size of the particle (breadth)
- `size_end:` The size multiplier. The particles size at the end of it's lifetime will be it's start size multiplied by this value
- `start_color_r:` The r (red) component of the start color of the particle
- `start_color_g:` The g (green) component of the start color of the particle
- `start_color_b:` The b (blue) component of the start color of the particle
- `start_color_a:` The a (alpha) component of the start color of the particle
- `gravity:` The (vertical) gravity applied to the particle
- `rotation:` The rotation applied to the particle. Rotation is only applied to the Y axis and it is specified in radians per second
- `velocity_var_x:` The x component of the start velocity variance of the particle
- `velocity_var_y:` The y component of the start velocity variance of the particle
- `velocity_var_z:` The z component of the start velocity variance of the particle
- `end_color_r:` The r (red) component of the end color of the particle
- `end_color_g:` The g (green) component of the end color of the particle
- `end_color_b:` The b (blue) component of the end color of the particle
- `end_color_a:` The a (alpha) component of the end color of the particle
- `emit_pos_var_x:` The x component of the start position variance of the particle
- `emit_pos_var_y:` The y component of the start position variance of the particle
- `emit_pos_var_z:` The z component of the start position variance of the particle
- `emit_pos_offset_x:` The x component of the start position offset of the particle
- `emit_pos_offset_y:` The y component of the start position offset of the particle
- `emit_pos_offset_z:` The z component of the start position offset of the particle

___

- Particles have a max duration (lifetime) of 8 seconds.
- The particles color is interpolated from start color to end color evenly across it's lifetime.
- emit_pos_var is randomized every emit. A value of 4 means any value between -4 to +4 could be added to the emit position
- `emit_pos_offset` and `emit_pos_var` are added to the particles start position to calculate the final start position


___

## Examples

```lua
add_particle(100,200,300,6,0.2,6,-0.8,1,2,0.5)
```

___

```lua
add_particle(100,200,300,6,0.2,6,-0.8,1,2,0.5,2,200,200,200,200,0.1,0.5,0.1,0.2,0.3,100,100,100,100,0.5,0.5,0.5,1,2,3)
```

___

### [back](../other)
