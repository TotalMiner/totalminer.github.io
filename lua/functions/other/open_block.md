
# (Official) LUA Scripting Documentation

## open_block

Open a block's interface screen.

___

Spec:

```lua
open_block(
	long x,
	long y,
	long z)
```

## Parameters

- `x`: The x component of the map point of the block.
- `y`: The y component of the map point of the block.
- `z`: The z component of the map point of the block.

___

## Example

```lua
local x,y,z = get_script_point()
open_block(x,y,z)
```

This example opens the interface screen of the script block that executed the script

___

#### Incomplete

This documentation is incomplete

___

### [back](../other)
