
# (Official) Console Documentation

## perm

Add or remove player permissions.

___

Add or remove permissions.

perm -a -r -l [permission1 permission2 ...]

-all  -- the command operates on all players.
-a  -- add the specified permission(s).
-r  -- remove the specified permission(s).
-l  -- list the current players permissions.
[permission1 permission2 ...]  -- a list of permissions to add or remove (separated by a space).

Example:
perm -l
List all permissions for the current player.

perm -l -all
List all permissions for all players.

perm -a creative fly
Add the Creative and Fly permissions to the current player.

perm -r scripts
Remove the Scripts permission from the current player.

perm -all -r map grief admin
Remove the map, grief, admin permissions from all players.

___

### [back](../commands)