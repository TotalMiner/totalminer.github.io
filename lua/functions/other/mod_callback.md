
# (Official) LUA Scripting Documentation

## mod_callback

A Mod callback. Call this function to pass string data to a mod.

___

Spec:

```lua
mod_callback(
	string mod_name,
	string data)
```

## Parameters

- `mod_name`: The name of the mod to call
- `data`: The string data to pass to the mod. This string can contain any data the mod requires

___

## Example

```lua
mod_callback("my mod","player has died")
```

___

##### Incomplete

This documentation is incomplete

___

### [back](../other)
