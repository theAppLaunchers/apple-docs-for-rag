

- SwiftUI
- GraphicsContext
-  fill(\_:with:style:) 

Instance Method

# fill(\_:with:style:)

Draws a path into the context and fills the outlined region.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
func fill(
    _ path: Path,
    with shading: GraphicsContext.Shading,
    style: FillStyle = FillStyle()
)
```

## Parameters 

`path`  

The outline of the region to fill.

`shading`  

The color or pattern to use when filling the region bounded by `path`.

`style`  

A style that indicates how to rasterize the path.

## Discussion

The current drawing state of the context defines the full drawing operation. For example, the current transformation and clip shapes, and any styles applied to the result, affect the final result.

## See Also

### Drawing a path

func stroke(Path, with: GraphicsContext.Shading, lineWidth: CGFloat)

Draws a path into the context with a specified line width.

func stroke(Path, with: GraphicsContext.Shading, style: StrokeStyle)

Draws a path into the context with a specified stroke style.

struct Shading

A color or pattern that you can use to outline or fill a path.

struct GradientOptions

Options that affect the rendering of color gradients.

