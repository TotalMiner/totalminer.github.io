# (Official) LUA Scripting Documentation

## Pages

- [Home](../../index)
- [Functions](../functions)

___

## LUA Data Types

TM Lua scripting primarily uses three data types.

- string: These data types store text, e.g. "Hello", "Body"
- integer (64bit): These data types store whole numbers, e.g. 1024, 10
- floating point number (64bit): These data types store numbers that have fractions, e.g. 10.25, 52.34553

Almost all TM Lua script commands will either accept or return one or more arguments of these three data types.

e.g:

```lua
local x,y,z = get_script_point()
set_block(x,y+2,z,block.wood)
```

In the example above, x,y,z and block.wood are integers.

___

## Block ID

The block id of the voxel. Block ID's are 8 bit integers.

## Aux

Auxiliary data for a voxel. Aux data is 8 bits.

## Light

Light data for a voxel. Light data is 8 bits.

- The first 4 bits are used for sunlight. Possible values are 0 to 15.
- The second 4 bits are used for block light, e.g. torches. Possible values are 0 to 15.
