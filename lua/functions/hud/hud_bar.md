
# (Official) LUA Scripting Documentation

## hud_bar

Add a hud bar. Hud bars are a form of progress bar.

___

Spec:

```lua
hud_bar(
	string name,
	bool is_player,
	string history,
	long max_value,
	NLua.LuaTable pos,
	NLua.LuaTable size,
	double scale,
	NLua.LuaTable color,
	string props)
```

## Parameters

- `name`: The name of the element. This name must be unique and is also used to remove the element
- `is_player`: True or False. If True this element is only shown on the context player's screen. If False, it is shown on all players screens
- `history`: The key/name of the history record to use as the progress value
- `max_value`: The progress value will be clamped to this maximum value
- `pos`: The screen coordinate of the element (Top Left udim2)
- `size`: The size of the element (udim2)
- `scale`: The scale of the text. Default = 1
- `color`: The color of the [progress] bar (color)
- `props`: Properties that define how the hud element is drawn

___

Valid values for props:
"vertical", "showlabel", "label", "shownumbers", "numbers",
"rightjustify", "right", "absolute", "abs", "cctv"

___

##### Incomplete

This documentation is incomplete

___

### [back](../hud)
