
# (Official) Console Documentation

## list

List various game information.

___

list: List various game information.

list -i -m -p -pe -s -tp -z [pattern]

-i   -- list all items in the current players inventory.
-m   -- list map markers.
-mg  -- list map grave markers.
-p   -- list all players in the world.
-pe  -- list the current players permissions.
-s   -- list scripts.
-tp  -- list the current players teleport points.
-z   -- list zones.

[pattern] -- any output that does not start with pattern is ignored. 
             e.g. list -i sa  -- list all items in inventory that start with 'sa'
                  list -p j  -- list all players whose name starts with 'j'

___

### [back](../commands)