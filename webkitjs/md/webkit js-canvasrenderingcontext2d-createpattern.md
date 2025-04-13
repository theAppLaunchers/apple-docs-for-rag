

- WebKit JS
- CanvasRenderingContext2D
-  createPattern 

Instance Method

# createPattern

Creates a pattern object using the specified image as a template. The pattern can be specified as repeating horizontally, vertically, both horizontally and vertically (the default), or not at all.

Safari Desktop 10.0+Safari Mobile 10.0+

``` source
CanvasPattern? createPattern(
    CanvasImageSource image, 
    DOMString repetition
);
```

## Parameters 

`image`  

An image object.

`repeat`  

An optional string. If the string value is `"repeat-x"`, the pattern repeats horizontally only. If the string value is `"repeat-y"`, the pattern repeats vertically only. If the string value is `"repeat-none"`, the pattern does not repeat. If this parameter is omitted, the pattern repeats both horizontally and vertically.

## Discussion

When specifying a stroke style or fill style, you can pass in a pattern object instead of a color. Subsequent drawing operations are stroked or filled using the specified image as a pattern. An image object can be obtained by setting a JavaScript variable equal to an HTML `img` element.

## See Also

### Creating Gradients and Patterns

createLinearGradient

Creates a linear gradient object with a specified start point and a specified end point.

createRadialGradient

Creates a radial gradient object using the cone defined by the specified starting and ending circles.

