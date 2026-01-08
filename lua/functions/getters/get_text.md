
# (Official) LUA Scripting Documentation

## get_text

Get the text of a block (Sign, Book, etc).

___

Spec:

```lua
get_text(
	long x,
	long y,
	long z,
	long page)
```

## Parameters

- `x`: The x component of the map point of the block.
- `y`: The y component of the map point of the block.
- `z`: The z component of the map point of the block.
- `page`: The page or line number. Defaults to 0 (Book title or all sign Text). 1-4 for individual lines of a sign.

## Returns

- `string`: Returns the text from the specified block. New lines are marked with an underscore "_".

___

## Examples

```lua
get_text(72, 240, 84, 0)
```

Pulls the text from the block at 72, 240, 84. If this block is a sign it would provide all text on it in the format of "LineOne_LineTwo_LineThree_LineFour". If it is a book it would provide just the title.

___

```lua
get_text(100, 52, 120, 3)
```

Pulls the text from the block at 100, 52, 120. If this block is a sign it would provide the third line of text. If it is a book it would provide the third page.

___

##### Incomplete

This documentation is incomplete

___

### [back](../getters)
