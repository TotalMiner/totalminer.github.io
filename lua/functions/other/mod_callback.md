
# (Official) LUA Scripting Documentation

## mod_callback

A Mod callback. Call this function to pass string data to a mod.

___

Spec:

```lua
mod_callback(
	string mod_id,
	string data)
```

## Parameters

- `mod_id`: The ID of the mod to call. This is specified in the mod's ModInfo.xml
- `data`: The string data to pass to the mod. This string can contain any data the mod requires

___

## Example

```lua
mod_callback("Example.MyMod", "player has died")
```

___

##### Incomplete

This documentation is incomplete

___

### [back](../other)
