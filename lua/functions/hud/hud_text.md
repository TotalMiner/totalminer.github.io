
# (Official) LUA Scripting Documentation

## hud_text

Add hud text.

___

Spec:

```lua
hud_text(
	string name,
	bool is_player,
	string text,
	udim2 pos,
	double scale,
	color color,
	double rot,
	string props)
```

## Parameters

- `name`: The name of the element. This name must be unique and is also used to remove the element
- `is_player`: True or False. If True this element is only shown on the context player's screen. If False, it is shown on all players screens
- `text`: 
- `pos`: The screen coordinate of the element (Top Left udim2)
- `scale`: The scale of the text. Default = 1
- `color`: The color of the text (color)
- `rot`: The rotation of the element in radians
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
