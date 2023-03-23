
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
	double x,
	double y,
	double w,
	double h,
	double scale,
	long r,
	long g,
	long b,
	long a,
	string props)
```

## Parameters

- `name`: The name of the element. This name must be unique and is also used to remove the element
- `is_player`: True or False. If True this element is only shown on the context player's screen. If False, it is shown on all players screens
- `history`: The key/name of the history record to use as the progress value
- `max_value`: The progress value will be clamped to this maximum value
- `x`: The x screen coordinate of the element
- `y`: The y screen coordinate of the element
- `w`: The width of the element
- `h`: The height of the element
- `scale`: The scale of the text. Default = 1
- `r`: The r (red) component of the elements color
- `g`: The g (green) component of the elements color
- `b`: The b (blue) component of the elements color
- `a`: The a (alpha) component of the elements color
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
