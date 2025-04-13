

- SwiftUI
- Color
-  init(\_:red:green:blue:opacity:) 

Initializer

# init(\_:red:green:blue:opacity:)

Creates a constant color from red, green, and blue component values.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
init(
    _ colorSpace: Color.RGBColorSpace = .sRGB,
    red: Double,
    green: Double,
    blue: Double,
    opacity: Double = 1
)
```

## Parameters 

`colorSpace`  

The profile that specifies how to interpret the color for display. The default is Color.RGBColorSpace.sRGB.

`red`  

The amount of red in the color.

`green`  

The amount of green in the color.

`blue`  

The amount of blue in the color.

`opacity`  

An optional degree of opacity, given in the range `0` to `1`. A value of `0` means 100% transparency, while a value of `1` means 100% opacity. The default is `1`.

## Discussion

This initializer creates a constant color that doesn’t change based on context. For example, it doesn’t have distinct light and dark appearances, unlike various system-defined colors, or a color that you load from an Asset Catalog with init(_:bundle:).

A standard sRGB color space clamps each color component — `red`, `green`, and `blue` — to a range of `0` to `1`, but SwiftUI colors use an extended sRGB color space, so you can use component values outside that range. This makes it possible to create colors using the Color.RGBColorSpace.sRGB or Color.RGBColorSpace.sRGBLinear color space that make full use of the wider gamut of a diplay that supports Color.RGBColorSpace.displayP3.

## See Also

### Creating a color from component values

init(hue: Double, saturation: Double, brightness: Double, opacity: Double)

Creates a constant color from hue, saturation, and brightness values.

init(Color.RGBColorSpace, white: Double, opacity: Double)

Creates a constant grayscale color.

enum RGBColorSpace

A profile that specifies how to interpret a color value for display.

