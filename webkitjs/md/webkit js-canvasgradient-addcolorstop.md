

- WebKit JS
- CanvasGradient
-  addColorStop 

Instance Method

# addColorStop

Adds a color to the gradient.

Safari Desktop 10.0+Safari Mobile 10.0+

``` source
void addColorStop(
    float offset, 
    DOMString color
);
```

## Parameters 

`offset`  

A number between 0 and 1, inclusive, representing the position on the gradient object where this color appears.

`color`  

A CSS color.

## Discussion

A gradient is a blend of colors, proceeding from one color stop to the next. You must add a color stop at offset 0 and a color stop at offset 1 before a gradient can be displayed. Adding color stops at 0 and 1 provides a beginning color and an ending color. You may add additional color stops between 0 and 1 to provide intermediate colors.

### Special Considerations

You cannot add a color stop at the same offset as an existing color stop. To change a color stop, obtain a new gradient instance and add the the color stops that you want.

