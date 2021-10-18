
# (Official) Console Documentation

## console

Edit console properties.

___

Adjust the position or size of the console window. 

console -fs -o -p -s [scale] [lines] [x] [y]

-fs [scale] -- Adjust the scale used to draw the console font. 0.75 = default. 

-o [lines]  -- Set how many lines of text are kept in the console output stream before they are dropped off the end. The default is 1000.

-p [x] [y]  -- Adjust the position of the console window. 
               x & y is the new screen position in pixels.

-s [x] [y]  -- Adjust the size of the console window. 
               x & y is the new size in columns and rows.

Examples:
console -p 20 50  -- changes the console screen position to 20 pixels across and 50 pixels down.
console -s 30 20  -- changes the console size to 30 characters wide and 20 rows high.
console -fs 0.5   -- makes the console font smaller.
console -o 500    -- set the consoles output stream size to 500 lines.

___

### [back](../commands)