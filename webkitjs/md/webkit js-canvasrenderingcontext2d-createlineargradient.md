

- WebKit JS
- CanvasRenderingContext2D
-  createLinearGradient 

Instance Method

# createLinearGradient

Creates a linear gradient object with a specified start point and a specified end point.

Safari Desktop 10.0+Safari Mobile 10.0+

``` source
CanvasGradient createLinearGradient(
    float x0, 
    float y0, 
    float x1, 
    float y1
);
```

## Parameters 

`x0`  

The x-coordinate of the starting point, in pixels from the left edge of the canvas coordinate system.

`y0`  

The y-coordinate of the starting point, in pixels from the top of the canvas coordinate system.

`x1`  

The x-coordinate of the ending point, in pixels from the left edge of the canvas coordinate system.

`y1`  

The y-coordinate of the ending point, in pixels from the top of the canvas coordinate system.

## Return Value

A linear gradient object.

## Discussion

You must add at least a starting and ending color stop to a linear gradient before it can be used. The direction of the gradient is specified by the start and end points. When setting the fill style or stroke style for drawing objects, you can pass in a linear gradient object instead of a color. Anything subsequently drawn or filled over the rectangle defined by the starting and ending points of the gradient are rendered using the gradient as a color. Anything drawn outside the rectangle is rendered using the color stop of the nearest edge of the rectangle. All parameter values are in the canvas’s current coordinate system, subject to the current transformation matrix (rotation, scale, and so on).

## See Also

### Creating Gradients and Patterns

createPattern

Creates a pattern object using the specified image as a template. The pattern can be specified as repeating horizontally, vertically, both horizontally and vertically (the default), or not at all.

createRadialGradient

Creates a radial gradient object using the cone defined by the specified starting and ending circles.

