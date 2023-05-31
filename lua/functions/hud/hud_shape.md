
# (Official) LUA Scripting Documentation

## hud_shape

Add a hud shape.

___

Spec:

```lua
hud_shape(
	string name,
	bool is_player,
	string shape,
	long item_id,
	udim2 pos,
	udim2 size,
	long bw,
	color color,
	color borderColor,
	string props)
```

## Parameters

- `name`: The name of the element. This name must be unique and is also used to remove the element
- `is_player`: True or False. If True this element is only shown on the context player's screen. If False, it is shown on all players screens
- `shape`: The type of shape. Currently only "rect" is supported
- `item_id`: If an item_id is specified, the texture for that item will be draw inside the element
- `pos`: The screen coordinate of the element (Top Left udim2)
- `size`: The size of the element (udim2)
- `bw`: The size of the elements border. Zero = no border
- `color`: The color of the shape (color)
- `borderColor`: The color of the shape border (color)
- `props`: Properties that define how the hud element is drawn

___

Valid values for shape: "rect"

Valid values for props:
"vertical", "showlabel", "label", "shownumbers", "numbers",
"rightjustify", "right", "absolute", "abs", "cctv"

___

##### Incomplete

This documentation is incomplete

___

### [back](../hud)
