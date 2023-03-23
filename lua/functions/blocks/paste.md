
# (Official) LUA Scripting Documentation

## paste

Paste a component.

___

Spec:

```lua
paste(
	string pack_name,
	string component_name,
	long x,
	long y,
	long z,
	string dir,
	string paste_type)
```

## Parameters

- `pack_name`: The name of the component pack in which the component is stored
- `component_name`: The name of the component
- `x`: The x component of the map point to paste the component
- `y`: The y component of the map point to paste the component
- `z`: The z component of the map point to paste the component
- `dir`: The direction to face the component for pasting
- `paste_type`: The type of paste.

___

## Example

```lua
Valid values for dir:
"left", "forward", "right", "back", "backward", "up", "down", "proxy", "proxydefault"

Valid values for paste_type:
"Overwrite": All source blocks are pasted (all destination blocks are overwritten).
"Merge": Only source blocks that are not empty are pasted.
"NoOverwrite": Only destination blocks that are empty are overwritten.
```

___

##### Incomplete

This documentation is incomplete

___

### [back](../blocks)
