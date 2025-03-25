
# (Official) LUA Scripting Documentation

## msgbox

Display a message box and wait for user input.

___

Spec:

```lua
msgbox(
	string heading,
	string body,
	string a_text,
	string x_text,
	string y_text,
	string b_text,
	bool vertical,
	bool no_cancel)
```

## Parameters

- `heading`: The message box header (title)
- `body`: The main body text of the message
- `a_text`: Text for the A button prompt
- `x_text`: Text for the X button prompt
- `y_text`: Text for the Y button prompt
- `b_text`: Text for the B butto prompt
- `vertical`: true = display button prompts vertically. Omit for default = false = display horizontally
- `no_cancel`: true/false, toggle if the close button is visible and if the menu can be closed without pressing any of the buttons. If no buttons are present the close button will be hidden but can still be closed with the appropriate keybind.

## Returns

- `long`: The number of the selected prompt. Zero = no selection (escape). 1 = A button, 2 = X button, 3 = Y button, 4 = B button.

___


Leaving an empty string for any of the button arguments will omit them from the message box.


___

##### Incomplete

This documentation is incomplete

___

### [back](../gui)
