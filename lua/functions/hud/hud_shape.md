
# (Official) LUA Scripting Documentation

## hud_shape

### Add a hud shape.

Spec:
```lua
hud_shape(
	name,
	is_player,
	shape,
	item_id,
	x,
	y,
	w,
	h,
	bw,
	r,
	g,
	b,
	a,
	br,
	bg,
	bb,
	ba,
	props)
```
## Parameters:
- `name:` The name of the element. This name must be unique and is also used to remove the element
- `is_player:` True or False. If True this element is only shown on the context player's screen. If False, it is shown on all players screens
- `shape:` The type of shape. Currently only "rect" is supported
- `item_id:` If an item_id is specified, the texture for that item will be draw inside the element
- `x:` The x screen coordinate of the element
- `y:` The y screen coordinate of the element
- `w:` The width of the element
- `h:` The height of the element
- `bw:` The size of the elements border. Zero = no border
- `r:` The r (red) component of the elements color
- `g:` The g (green) component of the elements color
- `b:` The b (blue) component of the elements color
- `a:` The a (alpha) component of the elements color
- `br:` The r (red) component of the elements border color
- `bg:` The g (green) component of the elements border color
- `bb:` The b (blue) component of the elements border color
- `ba:` The a (alpha) component of the elements border color
- `props:` Properties that define how the hud element is drawn

### [back](../hud)
