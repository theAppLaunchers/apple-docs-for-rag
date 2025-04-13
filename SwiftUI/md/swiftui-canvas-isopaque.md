

- SwiftUI
- Canvas
-  isOpaque 

Instance Property

# isOpaque

A Boolean that indicates whether the canvas is fully opaque.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
var isOpaque: Bool { get set }
```

## Discussion

You might be able to improve performance by setting this value to `true`, making the canvas is fully opaque. However, in that case, the result of drawing a non-opaque image into the canvas is undefined.

## See Also

### Managing opacity and color

var colorMode: ColorRenderingMode

The working color space and storage format of the canvas.

