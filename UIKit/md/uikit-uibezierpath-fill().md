

- UIKit
- UIBezierPath
-  fill() 

Instance Method

# fill()

Uses the current drawing properties to paint the region that the path encloses.

iOS 3.2+iPadOS 3.2+Mac Catalyst 13.1+tvOSvisionOS 1.0+watchOS 2.0+

``` source
func fill()
```

## Discussion

This method fills the path using the current fill color and drawing properties. If the path contains any open subpaths, this method implicitly closes them before painting the fill region.

The painted region includes the pixels right up to, but not including, the path line itself. For paths with large line widths, this can result in overlap between the fill region and the stroked path (which is itself centered on the path line).

This method automatically saves the current graphics state prior to drawing and restores that state when it is done, so you do not have to save the graphics state yourself.

## See Also

### Drawing paths

func fill(with: CGBlendMode, alpha: CGFloat)

Uses the specified blend mode and transparency values to paint the region that the path encloses.

func stroke()

Draws a line along the path using the current drawing properties.

func stroke(with: CGBlendMode, alpha: CGFloat)

Draws a line along the path using the specified blend mode and transparency values.

