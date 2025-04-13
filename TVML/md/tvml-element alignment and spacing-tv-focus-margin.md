

- TVML
- Element Alignment and Spacing
-  tv-focus-margin 

Article

# tv-focus-margin

Specifies the amount of space required for a custom cell element in focus.

## Overview

Important

`tv-focus-margin` can only be used with custom cell elements created in your binary.

### Values for tv-focus-margin

Integer  
The amount of space, in points, around each side of the cell indicating the room needed for a focusable, custom cell element.

Integer, Integer  
The amount of space, in points, around each side of the cell indicating the room needed for a focusable, custom cell element. The first value controls the top and bottom. The second value controls the left and right sides.

Integer, Integer, Integer  
The amount of space, in points, around each side of the cell indicating the room needed for a focusable, custom cell element. The first value controls the top. The second value controls the left and right sides. The third value controls the bottom.

Integer, Integer, Integer, Integer  
The amount of space, in points, around each side of the cell indicating the room needed for a focusable, custom cell element. The first value controls the top. The second value controls the right side. The third value controls the bottom. The fourth value controls the left side.

Note

You must explicitly set this style for custom cell elements provided by your app binary.

## See Also

### Element Spacing

margin

Specifies the spacing around an element.

padding

Specifies the padding between the border and contents of an element.

tv-interitem-spacing

Specifies the spacing between child elements.

tv-line-spacing

Specifies the amount of space between lines of text.

