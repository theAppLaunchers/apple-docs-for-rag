

- UIKit
- Drawing
- UIColor
-  Color creation 

API Collection

# Color creation

Load colors from asset catalogs and create colors from raw component values.

## Overview

Create color objects when you want to use specific colors in your UI, altering the raw component values used by grayscale, RGB, HSB, and CMYK. You can set the specified opacity and RGB component values to create personalized colors that fit your needs. Create colors dynamically by component values changing based on the currently active traits. You can use pattern colors to set the fill or stroke color.

## Topics

### Creating a color from component values

init(white: CGFloat, alpha: CGFloat)

Creates a color object using the specified opacity and grayscale values.

init(hue: CGFloat, saturation: CGFloat, brightness: CGFloat, alpha: CGFloat)

Creates a color object using the specified opacity and HSB color space component values.

init(red: CGFloat, green: CGFloat, blue: CGFloat, alpha: CGFloat)

Creates a color object using the specified opacity and RGB component values.

init(displayP3Red: CGFloat, green: CGFloat, blue: CGFloat, alpha: CGFloat)

Creates a color object using the specified opacity and RGB component values in the Display P3 color space.

init?(named: String)

Creates a color object using the information from the named asset.

init?(named: String, inBundle: Bundle?, compatibleWithTraitCollection: UITraitCollection?)

Creates a color object using the named asset that’s compatible with the specified trait collection.

### Creating a color dynamically

init(dynamicProvider: (UITraitCollection) -> UIColor)

Creates a color object that uses the specified block to generate its color data dynamically.

### Creating a color from another color object

convenience init(Color)

Creates a color object that encapsulates a SwiftUI color.

init(ciColor: CIColor)

Creates a color object that encapsulates a Core Image color.

init(cgColor: CGColor)

Creates a color object using the specified Quartz color reference.

func withAlphaComponent(CGFloat) -> UIColor

Creates a color object that has the same color space and component values as the receiver, but has the specified alpha component.

### Creating a pattern-based color

init(patternImage: UIImage)

Creates a color object using the specified image object.

### Creating a color from a resource

convenience init(resource: ColorResource)

## See Also

### Getting existing colors

UI element colors

Choose colors for UI elements such as labels, text, backgrounds, and links.

Standard colors

Define standard color objects for specific shades, such as red, blue, green, black, white, and more.

