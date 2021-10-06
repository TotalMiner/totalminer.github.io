# (Unofficial) XML Modding API Documentation

## Pages
- [Home](../index)
- [XML Documentation](xml-doc)
- [Data Types](data-types)
- [Adding and Modifying Items](items)
- [Modifying Blocks](blocks)
- [Adding and Modifying NPCs](npcs)
- [Adding Particle Templates](particles)

# Adding Particle Templates

Particle templates can be added with XML mods. These particle templates can be used with Particle Emitter blocks and scripts. Any field can be omitted to use defaults.
- [ParticleData.xml](#particledataxml)

---

## ParticleData.xml:

Contains the data for this particle template.

### Name: [string](data-types#string)

The name of this particle template. Use a backslash \(\\) to add a folder.

### EmitFreq: [int](data-types#int)

The time, in milliseconds, between spawns of this particle.

### Duration: [int](data-types#int)

The time, in milliseconds, this particle lasts.

### Rotation: [float](data-types#float)

The rotation speed of this particle.

### Velocity: [Vector3](data-types#vector3)

The initial velocity of this particle.

### VelocityVariance: [Vector3](data-types#vector3)

The random velocity that can be either added to or removed from this particle when spawned.

### EmitPosOffset: [Vector3](data-types#vector3)

The initial offset of this particle from the origin.

### EmitPosVariance: [Vector3](data-types#vector3)

The random offset that can be either added to or removed from this particle when spawned.

### Size: [Vector4](data-types#vector4)

The size of the particle, W being the end size multiplier.

### StartColor: [Color](data-types#color)

The intial color of the particle.

### EndColor: [Color](data-types#color)

The color of the particle at the end of its duration. The particle fades from the StartColor to this color.

### WindFactor: [float](data-types#float)

How much wind moves this particle.

### Gravity: [float](data-types#float)

How much gravity affects this particle.

#### [Table of Contents](#adding-particle-templates)