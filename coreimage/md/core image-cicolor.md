

- Core Image
-  CIColor 

Class

# CIColor

The component values defining a color in a specific color space.

iOS 5.0+iPadOS 5.0+Mac Catalyst 13.1+macOS 10.4+tvOS 9.0+visionOS 1.0+

``` source
class CIColor : NSObject
```

## Overview

You use `CIColor` objects in conjunction with other Core Image classes, such as CIFilter, CIContext, and CIImage, to take advantage of the built-in Core Image filters when processing images.

A color space defines a one-, two-, three-, or four-dimensional environment whose color components represent intensity values. A color component is also referred to as a *color channel*. An RGB color space, for example, is a three-dimensional color space whose stimuli are the red, green, and blue intensities that make up a given color. Regardless of the color space, in Core Image, color values range from `0.0` to `1.0`, with `0.0` representing an absence of that component (0 percent) and `1.0` representing 100 percent.

Colors also have an alpha component, which represents the opacity of the color, with `0.0` meaning completely transparent and `1.0` meaning completely opaque. If a color does not have an explicit alpha component, Core Image paints the color as if the alpha component equals `1.0`. You always provide unpremultiplied color components to Core Image, and Core Image then provides unpremultiplied color components to you. Core Image premultiplies each color component with the alpha value in order to optimize calculations. For more information on premultiplied alpha values, see Core Image Programming Guide.

## Topics

### Initializing Color Objects

init(cgColor: CGColor)

Initializes a Core Image color object with a Core Graphics color.

init(color: UIColor)

Initializes a Core Image color object using a UIKit (or AppKit) color object.

init(red: CGFloat, green: CGFloat, blue: CGFloat, alpha: CGFloat)

Initializes a Core Image color object with the specified red, green, blue, and alpha component values.

init?(red: CGFloat, green: CGFloat, blue: CGFloat, colorSpace: CGColorSpace)

Initializes a Core Image color object with the specified red, green, and blue component values as measured in the specified color space.

init?(red: CGFloat, green: CGFloat, blue: CGFloat, alpha: CGFloat, colorSpace: CGColorSpace)

Initializes a Core Image color object with the specified red, green, blue, and alpha component values as measured in the specified color space.

### Creating Color Objects

init(red: CGFloat, green: CGFloat, blue: CGFloat)

Creates a color object using the specified RGB color component values

init(string: String)

Creates a color object using the RGBA color component values specified by a string.

### Getting Color Components

var colorSpace: CGColorSpace

The Quartz 2D color space associated with the color.

var components: UnsafePointer&lt;CGFloat>

The color components of the color.

var numberOfComponents: Int

Returns the number of color components in the color.

var red: CGFloat

The unpremultiplied red component of the color.

var green: CGFloat

The unpremultiplied green component of the color.

var blue: CGFloat

The unpremultiplied blue component of the color.

var alpha: CGFloat

The alpha value of the color.

var stringRepresentation: String

A formatted string that specifies the components of the color.

### Creating a CIColor Object with Preset Components

class var black: CIColor

Returns a color object whose RGB values are all `0.0` and whose alpha value is `1.0`.

class var blue: CIColor

Returns a color object whose RGB values are `0.0`, `0.0`, and `1.0` and whose alpha value is `1.0`.

class var clear: CIColor

Returns a color object whose RGB and alpha values are all `0.0`.

class var cyan: CIColor

Returns a color object whose RGB values are `0.0`, `1.0`, and `1.0` and whose alpha value is `1.0`.

class var gray: CIColor

Returns a color object whose RGB values are all `0.5` and whose alpha value is `1.0`.

class var green: CIColor

Returns a color object whose RGB values are `0.0`, `1.0`, and `0.0` and whose alpha value is `1.0`.

class var magenta: CIColor

Returns a color object whose RGB values are `1.0`, `0.0`, and `1.0` and whose alpha value is `1.0`.

class var red: CIColor

Returns a color object whose RGB values are `1.0`, `0.0`, and `0.0` and whose alpha value is `1.0`.

class var white: CIColor

Returns a color object whose RGB values are all `1.0` and whose alpha value is `1.0`.

class var yellow: CIColor

Returns a color object whose RGB values are `1.0`, `1.0`, and `0.0` and whose alpha value is `1.0`.

## Relationships

### Inherits From

- NSObject

### Conforms To

- NSCopying
- NSSecureCoding

## See Also

### Filters

class CIFilter

An image processor that produces an image by manipulating one or more input images or by generating new image data.

class CIRAWFilter

A filter subclass that produces an image by manipulating RAW image sensor data from a digital camera or scanner.

class CIVector

A container for coordinate values, direction vectors, matrices, and other non-scalar values, typically used in Core Image for filter parameters.

