

- SwiftUI
- GraphicsContext
- GraphicsContext.Filter
-  saturation(\_:) 

Type Method

# saturation(\_:)

Returns a filter that applies a saturation adjustment.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
static func saturation(_ amount: Double) -> GraphicsContext.Filter
```

## Parameters 

`amount`  

The amount of the saturation adjustment. A value of zero to completely desaturates each pixel, while a value of one makes no change. You can use values greater than one.

## Return Value

A filter that applies a saturation adjustment.

## Discussion

This filter is equivalent to the `saturate` filter primitive defined by the Scalable Vector Graphics (SVG) specification.

## See Also

### Manipulating color

static func colorInvert(Double) -> GraphicsContext.Filter

Returns a filter that inverts the color of their results.

static func colorMultiply(Color) -> GraphicsContext.Filter

Returns a filter that multiplies each color component by the matching component of a given color.

static func hueRotation(Angle) -> GraphicsContext.Filter

Returns a filter that applies a hue rotation adjustment.

static func grayscale(Double) -> GraphicsContext.Filter

Returns a filter that applies a grayscale adjustment.

static func colorMatrix(ColorMatrix) -> GraphicsContext.Filter

Returns a filter that multiplies by a given color matrix.

