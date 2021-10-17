# (Official) LUA Scripting Documentation

## Pages

- [Home](../../index)
- [Functions](functions)

___

## Data Types

TM Lua scripting primarily uses three data types.

- string: These data types store text, e.g. \"Hello\", \"Body\", \"Left\"
- integer(64bit): These data types store whole numbers only, e.g. 1024, 10, 123
- floating point number(64bit): These data types store numbers that can have fractions, e.g. 10.25, 52.34553, 100.0
- bool: These data types store only two possible values, either `true` or `false`. They are typically used to indicate if something is true or not.

Almost all TM Lua script functions / commands will accept and / or return one or more arguments of these three data types.

e.g:

```lua
local x,y,z = get_script_point()
set_block(x, y + 2, z, block.wood)
```

In the example above, x, y, z and block.wood are integers.

___

```lua
equip(item.woodsword, \"right\")
```

In the example above, item.woodsword is an integer and \"right\" is a string.

___

```lua
local x,y,z = get_pos()
```

In the example above, x, y, z are floating point numbers.

___

## Block ID

The block id of the voxel.Block ID's are 8 bit integers.

## Aux

Auxiliary data for a voxel. Aux data is 8 bits.

## Light

Light data for a voxel. Light data is 8 bits.

- The first 4 bits are used for sunlight.Possible values are 0 to 15.
- The second 4 bits are used for block light, e.g.torches.Possible values are 0 to 15.
