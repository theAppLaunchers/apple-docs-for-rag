

- TVML
- Element Shaping
-  border-radius 

Article

# border-radius

Changes the shape of an element’s corner.

## Overview

Use the `border-radius` style to apply rounded corners to elements. Here’s an example that changes the border radius of an `img` element.

```

   Movie 1

```

### Values for border-radius

4-tuple  
An image whose corners are cropped to the specified radius.

`circle`  
An image that is cropped to fit inside of a circle.

`large`  
An image whose corners are cropped to create rounded corners with a large radius.

`medium`  
An images whose corners are cropped to create rounded corners with a medium radius.

`small`  
An images whose corners are cropped to create rounded corners with a small radius.

There are four ways to designate the border-radius style as a 4-tuple:

- `border-radius: X1 X2 X3 X4`—Where X1 is applied to the top-left corner, X2 is applied to the top-right corner, X3 is applied to the bottom-right corner, and X4 is applied to the bottom-left corner.

- `border-radius: X1 X2 X3`—Where X1 is applied to the top-left corner, X2 is applied to the top-right and bottom-left corners, and X3 is applied to the bottom-right corner.

- `border-radius: X1 X2`—Where X1 is applied to the top-left and bottom-right corners, and X2 is applied to the top-right and bottom-left corners.

- `border-radius: X1`—Where X1 is applied to each corner.

### Elements that Use border-radius

- card

- heroImg

- img

- monogram

- ratingCard

- reviewCard

- textBadge

