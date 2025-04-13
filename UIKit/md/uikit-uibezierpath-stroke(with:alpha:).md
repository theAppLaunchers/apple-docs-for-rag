

- UIKit
- UIBezierPath
-  stroke(with:alpha:) 

Instance Method

# stroke(with:alpha:)

Draws a line along the path using the specified blend mode and transparency values.

iOS 3.2+iPadOS 3.2+Mac Catalyst 13.1+tvOSvisionOS 1.0+watchOS 2.0+

``` source
func stroke(
    with blendMode: CGBlendMode,
    alpha: CGFloat
)
```

## Parameters 

`blendMode`  

The blend mode determines how the stroked path is composited with any existing rendered content.

`alpha`  

The amount of transparency to apply to the stroked path. Values can range between `0.0` (transparent) and `1.0` (opaque). Values outside this range are clamped to `0.0` or `1.0`.

## Discussion

The drawn line is centered on the path with its sides parallel to the path segment. This method applies the current stroke color and drawing properties (plus the specified blend mode and transparency value) to the rendered path.

This method automatically saves the current graphics state prior to drawing and restores that state when it is done, so you do not have to save the graphics state yourself.

## See Also

### Drawing paths

func fill()

Uses the current drawing properties to paint the region that the path encloses.

func fill(with: CGBlendMode, alpha: CGFloat)

Uses the specified blend mode and transparency values to paint the region that the path encloses.

func stroke()

Draws a line along the path using the current drawing properties.

