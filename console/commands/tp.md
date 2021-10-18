
# (Official) Console Documentation

## tp

Teleport the current player or manipulate teleport points.

___

Teleport the current player or manipulate teleport points.

tp -a -r -ra [name]

-a   -- Add a teleport point for the current player (where the current player is currently standing).
-r   -- Remove the named teleport point for the current player.
-ra  -- Remove all teleport points from the current player.
[name]  -- Name of the teleport point or map marker.

Examples:
tp home  -- teleport the current player to the teleport point or map marker named 'home'.
tp -a home  -- add the teleport point 'home' to the current player.
tp -r home  -- remove the teleport point 'home' for the current player.
tp -ra  -- remove all teleport points from the current player.

___

### [back](../commands)