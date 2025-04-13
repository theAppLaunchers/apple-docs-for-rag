

- ClockKit
-  CLKImageProvider Deprecated

Class

# CLKImageProvider

An image displayed by a complication.

watchOS 2.0–9.0Deprecated

``` source
class CLKImageProvider
```

Deprecated

Use WidgetKit to create complications for watchOS 10 or later. For more information, see Migrating to WidgetKit.

## Mentioned in 

Creating a timeline entry

## Overview

You create an image provider with at least one image, and you may specify two additional images to use under certain conditions. The specified images are *template images*, with a color applied to them prior to display. The clock face displaying the complication determines how the images are composited together and which tint color is applied.

Every image provider must contain a *one-piece image*, composed of a single template image. In multicolor classic complications, ClockKit applies the color in the tintColor property to your template image and displays the results in your complication. If you don’t specify a value for the tintColor property, the image provider applies the tint color associated with the underlying template or white if the template doesn’t specify a color. In tinted graphic complications, ClockKit ignores the tintColor property, and applies the color associated with the watch face.

In addition to the one-piece image, you may optionally specify two additional images to composite together in order to create a single final image. A two-piece image consists of a foreground image layered on top of a background image. Both images are template images. For classic complications, ClockKit applies the color in the tintColor property to the background image, falling back to the color in the underlying template or white if the template doesn’t specify a color. For tinted graphic complications, the system determines the color according to the user’s color selection. In classic complications, two-piece images take priority over one-piece images. In tinted graphic complications, the system can choose either the one-piece or two-piece image, based on the complication and watch face.

For information about image sizes to use in different templates, see Apple Watch Human Interface Guidelines.

## Topics

### Creating an Image Provider

convenience init(onePieceImage: UIImage)

Creates and returns an image provider with the specified one-piece image.

convenience init(onePieceImage: UIImage, twoPieceImageBackground: UIImage?, twoPieceImageForeground: UIImage?)

Creates and returns an image provider with both one-piece and two-piece images.

### Getting the Image Data

var onePieceImage: UIImage

The template image to use as a one-piece image.

var tintColor: UIColor?

The tint color to apply to the image in a multicolor clock face.

var twoPieceImageBackground: UIImage?

The background image in a two-piece image.

var twoPieceImageForeground: UIImage?

The foreground image in a two-piece image.

### Setting the Accessibility Label

var accessibilityLabel: String?

A succinct label that succinctly identifies the purpose of the image.

### Creating Empty Image Providers

class func new() -> Self

Creates an empty image provider.

init()

Creates an empty image provider.

## Relationships

### Inherits From

- NSObject

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSCopying
- NSObjectProtocol

## See Also

### Image providers

class CLKFullColorImageProvider

A full-color image displayed by a complication.

Deprecated

