
# (Official) LUA Scripting Documentation

## add_particle_emitter

Add a Particle Emitter.

___

Spec:

```lua
add_particle_emitter(
	double x,
	double y,
	double z,
	double emitter_duration,
	double emit_freq,
	double particle_duration,
	double velocity_x,
	double velocity_y,
	double velocity_z,
	double size_x,
	double size_y,
	double size_z,
	double size_end,
	long start_color_r,
	long start_color_g,
	long start_color_b,
	long start_color_a,
	double gravity,
	double rotation,
	double velocity_var_x,
	double velocity_var_y,
	double velocity_var_z,
	long end_color_r,
	long end_color_g,
	long end_color_b,
	long end_color_a,
	double emit_pos_var_x,
	double emit_pos_var_y,
	double emit_pos_var_z,
	double emit_pos_offset_x,
	double emit_pos_offset_y,
	double emit_pos_offset_z)
```

## Parameters

- `x`: The x component of the world position of the emitter. This is also the base start position of all emitted particles.
- `y`: The y component of the world position of the emitter. This is also the base start position of all emitted particles.
- `z`: The z component of the world position of the emitter. This is also the base start position of all emitted particles.
- `emitter_duration`: The duration of the emitter in seconds
- `emit_freq`: A new particle is emitted at this frequency (in milliseconds)
- `particle_duration`: The duration (lifetime) of the particle in seconds.
- `velocity_x`: The x component of the base start velocity of the particle
- `velocity_y`: The y component of the base start velocity of the particle
- `velocity_z`: The z component of the base start velocity of the particle
- `size_x`: The x component of the start size of the particle (width)
- `size_y`: The y component of the start size of the particle (height)
- `size_z`: The z component of the start size of the particle (breadth)
- `size_end`: The size multiplier. The particles size at the end of it's lifetime will be it's start size multiplied by this value
- `start_color_r`: The r (red) component of the start color of the particle
- `start_color_g`: The g (green) component of the start color of the particle
- `start_color_b`: The b (blue) component of the start color of the particle
- `start_color_a`: The a (alpha) component of the start color of the particle
- `gravity`: The (vertical) gravity applied to the particle
- `rotation`: The rotation applied to the particle. Rotation is only applied to the Y axis and it is specified in radians per second
- `velocity_var_x`: The x component of the start velocity variance of the particle
- `velocity_var_y`: The y component of the start velocity variance of the particle
- `velocity_var_z`: The z component of the start velocity variance of the particle
- `end_color_r`: The r (red) component of the end color of the particle
- `end_color_g`: The g (green) component of the end color of the particle
- `end_color_b`: The b (blue) component of the end color of the particle
- `end_color_a`: The a (alpha) component of the end color of the particle
- `emit_pos_var_x`: The x component of the start position variance of the particle
- `emit_pos_var_y`: The y component of the start position variance of the particle
- `emit_pos_var_z`: The z component of the start position variance of the particle
- `emit_pos_offset_x`: The x component of the start position offset of the particle
- `emit_pos_offset_y`: The y component of the start position offset of the particle
- `emit_pos_offset_z`: The z component of the start position offset of the particle

___

- The emitter is removed after `duration` seconds.
- Particles have a max duration (lifetime) of 8 seconds.
- The particles color is interpolated from start color to end color evenly across it's lifetime.
- emit_pos_var is randomized every emit. A value of 4 means any value between -4 to +4 could be added to the emit position
- `emit_pos_offset` and `emit_pos_var` are added to the particles start position to calculate the final start position


___

## Example

```lua
add_particle_emitter(100,200,300,60,1,6,0.2,6,-0.8,1,2,0.5,2,200,200,200,200,0.1,0.5,0.1,0.2,0.3,100,100,100,100,0.5,0.5,0.5,1,2,3)
```

___

##### Incomplete

This documentation is incomplete

___

### [back](../particles)
