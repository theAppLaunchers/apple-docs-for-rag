

- UIKit
- Drawing
- UIColor
-  UI element colors 

API Collection

# UI element colors

Choose colors for UI elements such as labels, text, backgrounds, and links.

## Overview

UIKit provides color objects for the foreground and background colors of your app’s UI elements. The names of these color objects reflect their intended use, rather than specific color values.

Except where noted, the color objects adapt automatically to Dark Mode changes when you use the provided UIColor object. If you retrieve the color values, either directly or using another type such as CGColor, you must handle Dark Mode changes yourself. For more information about supporting Dark Mode, see Supporting Dark Mode in Your Interface.

## Topics

### Label colors

class var label: UIColor

The color for text labels that contain primary content.

class var secondaryLabel: UIColor

The color for text labels that contain secondary content.

class var tertiaryLabel: UIColor

The color for text labels that contain tertiary content.

class var quaternaryLabel: UIColor

The color for text labels that contain quaternary content.

### Fill colors

class var systemFill: UIColor

An overlay fill color for thin and small shapes.

class var secondarySystemFill: UIColor

An overlay fill color for medium-size shapes.

class var tertiarySystemFill: UIColor

An overlay fill color for large shapes.

class var quaternarySystemFill: UIColor

An overlay fill color for large areas that contain complex content.

### Text colors

class var placeholderText: UIColor

The color for placeholder text in controls or text views.

### Tint color

class var tintColor: UIColor

A color value that resolves at runtime based on the current tint color of the app or trait hierarchy.

### Standard content background colors

class var systemBackground: UIColor

The color for the main background of your interface.

class var secondarySystemBackground: UIColor

The color for content layered on top of the main background.

class var tertiarySystemBackground: UIColor

The color for content layered on top of secondary backgrounds.

### Grouped content background colors

class var systemGroupedBackground: UIColor

The color for the main background of your grouped interface.

class var secondarySystemGroupedBackground: UIColor

The color for content layered on top of the main background of your grouped interface.

class var tertiarySystemGroupedBackground: UIColor

The color for content layered on top of secondary backgrounds of your grouped interface.

### Separator colors

class var separator: UIColor

The color for thin borders or divider lines that allows some underlying content to be visible.

class var opaqueSeparator: UIColor

The color for borders or divider lines that hides any underlying content.

### Link color

class var link: UIColor

The specified color for links.

### Nonadaptable colors

class var darkText: UIColor

The nonadaptable system color for text on a light background.

class var lightText: UIColor

The nonadaptable system color for text on a dark background.

### Deprecated colors

class var groupTableViewBackground: UIColor

The system color to use for the background of a grouped table.

Deprecated

## See Also

### Getting existing colors

Standard colors

Define standard color objects for specific shades, such as red, blue, green, black, white, and more.

Color creation

Load colors from asset catalogs and create colors from raw component values.

