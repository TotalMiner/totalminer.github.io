
# (Official) LUA Scripting Documentation

## hud_counter

Add a hud counter. A hud counter is a form of text progress counter.

___

Spec:

```lua
hud_counter(
	string name,
	bool is_player,
	string history,
	udim2 pos,
	double scale,
	color color,
	string props)
```

## Parameters

- `name`: The name of the element. This name must be unique and is also used to remove the element
- `is_player`: True or False. If True this element is only shown on the context player's screen. If False, it is shown on all players screens
- `history`: The key/name of the history record to use as the counter value
- `pos`: The screen coordinate of the element (Top Left udim2)
- `scale`: The scale of the text. Default = 1
- `color`: The color of the text (color)
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
