# (Unofficial) XML Modding API Documentation

## Pages
- [Home](../index)
- [XML Documentation](xml-doc)
- [Data Types](data-types)
- [Adding and Modifying Items](items)
- [Modifying Blocks](blocks)
- [Adding and Modifying NPCs](npcs)
- [Adding Particle Templates](particles)

# Adding And Modifying NPCs

NPCs, also known as Actors, can be added and modified with XML mods. If the NPC ID supplied already exists, that NPC will be modified. Below is the documentation for each file used to add or modify NPCs. Any file or field can be omitted to use default values.
- [ActorTypeData.xml](#actortypedataxml)
- [ActorAIData.xml](#actoraidataxml)
- [ActorAudioData.xml](#actoraudiodataxml)
- [ActorLevelData.xml](#actorleveldataxml)
- [ActorPhysicsData.xml](#actorphysicsdataxml)

---

## ActorTypeData.xml:

Contains general information about this NPC.

### ActorType: ActorType

The ID of this NPC. If this is an existing NPC, that NPC will be modified, otherwise this NPC will be added.

### LevelType: [ActorLevelType](#actorleveldataxml)

The level type of this NPC.

### PhysicsType: [ActorPhysicsType](#actorphysicsdataxml)

The physics type of this NPC.

### AIType: [ActorAIType](#actoraidataxml)

The AI type of this NPC.

### ComName: [string](data-types#string)

The name of the component this NPC uses for its model.

### ComNameWalk: [string](data-types#string)\[\]

(Experimental) An array of components this NPC switches between when walking.

### ModelHeight: [float](data-types#float)

The height of NPC, in blocks. The width of the NPC will stretch to accomodate to this height.

### ModelYRotation: [float](data-types#float)

The rotation of the NPC's model along the Y axis. 3.1416 (Pi) = 180 degrees

### IsValid: [bool](data-types#bool)

If false, this NPC cannot be spawned, effectively removing the NPC.

### IsFemale: [bool](data-types#bool)

If true, this NPC should be considered female.

### IsPassive: [bool](data-types#bool)

If true, this NPC will only spawn if passive mob spawns are enabled. If false, this NPC will only spawn if hostile mob spawns are enabled.

### IsImmuneToFire: [bool](data-types#bool)

If true, this NPC will not take damage from fire or lava.

### HasNameplate: [bool](data-types#bool)

If false, this NPC will never have a visible nameplate.

### HandMaxHit: [int](data-types#int)

The maximum damage this NPC can deal without a weapon.

### NaturalSpawnFreq: [float](data-types#float)

The time, in seconds, between spawns of this NPC. If this is 0, this NPC cannot spawn naturally.

### NaturalBehavior: [string](data-types#string)

The behavior this NPC has when naturally spawned.

### LootTable: [LootItem](/data-types#lootitem)\[\]

An array of items that this NPC can drop when killed.

#### [Table of Contents](#adding-and-modifying-npcs)

---

## ActorAIData.xml:

Contains information about this NPC's AI.

### ActorAIType: ActorAIType

The ID of this AI Type. If this is an existing AI Types, that AI Type will be modified, otherwise this AI Type will be added.

### StrikeDelay: [float](data-types#float)

The time, in seconds, between attacks of an NPC with this AI Type.

### StrikeRange: [float](data-types#float)

The distance, in blocks, of this attacks of an NPC with this AI Type.

### RegardRange: [int](data-types#int)

The distance, in blocks, that an NPC with this AI Type will notice a target.

### HearingRange: [int](data-types#int)

The distance, in blocks, that an NPC with this AI Type will hear a target.

### AttackRange: [int](data-types#int)

The distance, in blocks, that an NPC with this AI Type will try attacking and moving to attack a target.

### InactiveRange: [int](data-types#int)

The distance, in blocks, that all players must be from an NPC with this AI Type for it to despawn.

#### [Table of Contents](#adding-and-modifying-npcs)

---

## ActorAudioData.xml:

Contains information about the sounds this NPC makes.

### ActorType: ActorType

The ID of this NPC. If this is an existing NPC, that NPC will be modified, otherwise this NPC will be added.

### AudioPain: [string](data-types#string)

The sound this NPC makes when attacked.

### AudioStrike: [string](data-types#string)

Currently unused.

### AudioWarning: [string](data-types#string)

The sound this NPC makes when warning a target. Currently only used when milking a cow.

### AudioDeath: [string](data-types#string)

The sound this NPC makes when killed.

#### [Table of Contents](#adding-and-modifying-npcs)

---

## ActorLevelData.xml:

Contains information about this NPC's skill levels.

### ActorLevelType: ActorLevelType

The ID of this Level Type. If this is an existing Level Type, that Level Type will be modified, otherwise this Level Type will be added.

### HealthLevel: [int](data-types#int)

The default health level of an NPC with this Level Type. NPCs have a base health of 10 at health level 1, and every health level under level 100 adds 3 health. Every health level at level 100 or above adds 1 health.

### AttackLevel: [int](data-types#int)

The default attack level of an NPC with this Level Type.

### StrengthLevel: [int](data-types#int)

The default strength level of an NPC with this Level Type.

### DefenceLevel: [int](data-types#int)

The default defence level of an NPC with this Level Type.

### RangedLevel: [int](data-types#int)

The default ranged level of an NPC with this Level Type.

#### [Table of Contents](#adding-and-modifying-npcs)

---

## ActorPhysicsData.xml:

Contains information about this NPC's movement.

### ActorPhysicsType: ActorPhysicsType

The ID of this Physics Type. If this is an existing Physics Type, that Physics Type will be modified, otherwise this Physics Type will be added.

### Acceleration: [float](data-types#float)

The speed an NPC of this Physics Type moves at when walking. Blocks/s = Acceleration * 60

### MoveSpeed: [float](data-types#float)

The maximum speed an NPC with this Physics Type can move at.

### JumpSpeed: [float](data-types#float)

The strength of an NPC with this Physics Type's jump.

### RotateSpeed: [float](data-types#float)

The speed an NPC with this Physics Type rotates at when turning and looking around.

#### [Table of Contents](#adding-and-modifying-npcs)