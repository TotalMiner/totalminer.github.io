
# (Official) LUA Scripting Documentation

## require

Load a library.

___

Spec:

```lua
require(
	string name)
```

## Parameters

- `name`: The name of the library

## Returns

- `ref`: A reference to the library

___

## Examples

```lua
local lib = require("my_lib")
lib.hello()
```

And below is the library code in 'library\my_lib_lua'

___

```lua
local lib = { }

function lib.hello()
print("hello")
end

return lib
```

___

##### Incomplete

This documentation is incomplete

___

### [back](../other)
