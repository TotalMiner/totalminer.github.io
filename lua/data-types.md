# (Official) LUA Scripting Documentation

## Pages

- [Home](../../index)
- [Functions](functions)

___

- [Block ID](#block-id)
- [Aux Data](#aux-data)
- [Light Data](#light-data)
- [Enums](#enums)
- [Vectors](#vectors)
- [HUD Types](#hud-types)

___

## Data Types

Scripts written using Lua will primarily use four data types.

- `bool`: These data types can store only two possible values, either `true` or `false`. They are typically used to indicate if something is true or not.

- `string`: These data types store text, e.g. "Hello", "Body", "Left". Some  functions require strings as parameters to specify how to process other data.

- `integer` (64bit): These data types store whole numbers only, e.g. 1024, 10, 123

- `floating point number` (64bit): These data types store numbers that can have fractions, e.g. 10.25, 52.34553, 100.0

Almost all TM Lua script functions / commands will accept and / or return one or more arguments of these four data types.

e.g:

```lua
local x,y,z = get_script_point()
set_block(x,y+2,z,block.wood)
```

In the example above, x, y, z and block.wood are integers.

___

```lua
equip(item.woodsword,"right")
```

In the example above, item.woodsword is an integer and "right" is a string. This example shows how a string parameter defines what to do with another argument, i.e. `"right"` is telling the `equip` function to equip the `wood sword` into the actors `right` hand.

___

```lua
local x,y,z = get_pos()
```

In the example above, x, y, z are floating point numbers.

___

## Block ID

A block id is an 8 bit integer and used to specify which block is present at a map point. Because they are 8 bit integers, there are 256 possible block id's (0 - 255).

A block id of zero (0) defines empty space (no block).

There is a global enum called `block` which defines the integer value for every block id in the game. You can use this enum to specify a block id, rather than having to know/use the actual integer value.

```lua
local x,y,z = get_point() -- the map point of the players foot position
local block_id = get_block(x,y-1,z) -- get the block id immediately below the players feet
if block_id == block.grass
then notify("you are standing on grass")
else notify("you are not standing on grass")
end
```

```lua
local x,y,z = get_point() -- the map point of the players foot position
set_block(x,y-1,z,block.marble) -- set the block under foot to marble
```

```lua
local x,y,z = get_point() -- the map point of the players foot position
set_block(x,y-1,z,0) -- clear the block under foot
  set_block(x,y-1,z, block.none) -- exactly the same as line above
```

___

## Aux Data

Auxillary data is an 8 bit integer and it is used to store extra data about a voxel.

The actual data stored differs depending on the block id. Many block id's do not use auxillary data.

There is one use of auxillary data that is common to all block id's. This is a 1 bit flag that indicates if the block at a voxel point is the original block placed there by world generation, or if it has been `changed` since. This is the 4th bit of the aux value. If the 4th bit is zero (0), then the block at that point is the original block from world generation. If the 4th bit is one (1), then that voxel point has been edited after world generation.

Other uses for aux data are `rotation` and `re-texture`.

`Rotation` uses the first 2 or 3 bits. Typically the first 2 bits define the horizontal rotation of the block (around the Y axis), and the 3rd bit defines if the block is upside down. Not all rotatable blocks use the 3rd bit.

`Re-texture` uses the last 4 bits of aux data (bit 5 - 8). The re-texture value is an integer between 0 and 15 and specifies which of the 16 possible re-texture slots are used for this block/point.

Aux data is retrieved using the `get_aux` function;

```lua
local x,y,z = get_eye_pos()
local aux = get_aux(x,y,z)-- get the aux data
```

___

## Light Data

Light data is an 8 bit integer.

Light data is split into two 4 bit integer parts. As each part is 4 bits, they can each store a number from 0 to 15. Zero (0) indicates no light, 15 indicates maximum light.

- The first 4 bits are used for `sunlight`
- The second 4 bits are used for `block light`, or light emitted from blocks, e.g.`torches`, `sunbox`, etc.

Light data is retrieved using the get_light functions

```lua
local x,y,z = get_eye_pos()
local light = get_light(x,y,z)-- get the full 8 bit light data
local sun_light = get_sun_light(x,y,z) -- get the 4 bit sun light data
local block_light = get_block_light(x,y,z)-- get the 4 bit block light data
```

___

## Enums

There are two `global` enums predefined for use in lua scripts.

- `block`
- `item`

`block` defines the integer value for every block name (block id) in the game.

`item` defines the integer value for every item name (item id) in the game.

These enums can be used in place of the actual integer values for blocks and items.

nb. the `item` enum defines values for both block and items.

e.g.

```lua
local x,y,z = get_point() -- the map point of the players foot position
set_block(x,y-1,z,block.marble) -- set the block under foot to marble
```

```lua
add_inventory(item.woodsword, 1)
add_inventory(item.leatherhelmet)
equip(item.woodsword,"right")
equip(item.leatherhelmet,"body")
add_inventory(block.basalt)
add_inventory(item.basalt) -- same as line above
```

___

## Vectors

Vectors are useful data types often used in games. They are typically used to store `positions`, `velocities` and `directions`.

Two vector types are predefined for your convenience.

- `vec2` a two component vector. contains an x and y value. Used for 2D values.
- `vec3` a three component vector. contains an x, y and z value. Used for 3D values.

These types are provided because vector math is easier to learn and use than euler equivalents for directional calculations 

e.g. to calculate a point 50 blocks directly ahead of the players camera

```lua
local eye_pos = vec3(get_eye_pos())
local view_dir = vec3(get_view_dir())
local target_pos = eye_pos + view_dir * 50
```

and here is the long version of the same thing (for clarity)

```lua
local ex,ey,ez = get_eye_pos()
local eye_pos = vec3(ex,ey,ez)
local vx, vy, vz = get_view_dir()
local view_dir = vec3(vx,vy,vz)
local target_pos = eye_pos + view_dir * 50
```

___

## HUD types

There are two data types specifically for handling HUD elements.

- `udim2` a 4 component data type. contains values for the x scale, x offset and y scale, y offset of a HUD element position and size.
- `color` a 4 component data type. contains values for the red, green, blue and alpha components of a color.

### udim2

A udim2 variable holds a scale and an offset for both the x and y axis (4 values in total).

If you are familiar with Roblox scripting, this is the same thing.

The scale value is resolution independent and ranges from 0 to 1. 0 = the left/top edge of the screen, 0.5 = the center of the screen, and 1 = the right/bottom edge of the screen, regardless of the screen resolution.
The offset value is the number of pixels to offset the scale value. It can be a negative value, offseting to the left or above the scale value, it can be 0, no offset, or it can be a positive value, offseting to the right or below the scale value.

You can use just the scale value, just the offset value (not resolution independent) or you can use a combination of both.

```lua
local left_top = udim2(0,0,0,0)
local left_middle = udim2(0,0,0.5,0)  -- y scale = 0.5
local right_bottom = udim2(1,0,1,0)  -- x and y scale = 1
local screen_center = udim2(0.5,0,0.5,0)  -- x and y scale = 0.5
local screen_center_offset = udim2(0.5,-100,0.5,60)  -- center of screen offset 100 pixels to the left and 60 pixels down
```

And udims are also used to describe HUD element sizes.
eg. below describes a rectangle that is a quarter of the screen in size and centered in the middle.
```lua
local pos = udim(0.25,0,0.25,0)
local size = udim(0.5,0,0.5,0)
```
Try to understand why the position is using a scale of 0.25 and the size is using a scale of 0.5 even though the element is a quarter of the screen size and centered.
It might help to understand by adding the two values together to calculate what the right bottom edge udim2 would be.


### color

A color variable holds 4 values, for the red, green, blue and alpha components of a color (in that order)
Each value is typically between 0 and 255.
The alpha value is for transparency. An alpha value of 0 will be fully transparent (invisible), a value of 128 is half transparent (semi-see-through) and a value of 255 is fully opaque (not see through).

```lua
local red = color(255,0,0,255)  -- Red, fully opaque
local blue = color(0,0,255,128)  -- Blue, semi-transparent
local white = color(255,255,255,128)  -- Bright White, semi-transparent
local gray = color(125,125,125,255)  -- Gray, opaque
local black = color(0,0,0,255)  -- Black, opaque
local trans = color(0,0,0,0)  -- Transparent, invisible, fully transparent
```

___

##### Incomplete

This documentation is incomplete
