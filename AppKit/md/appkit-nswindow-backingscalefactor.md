

- AppKit
- NSWindow
-  backingScaleFactor 

Instance Property

# backingScaleFactor

The backing scale factor.

macOS 10.7+

``` source
@MainActor
var backingScaleFactor: CGFloat { get }
```

## Discussion

The value of this property is `2.0` for high-resolution scaled display modes, and `1.0` for all other cases.

There are some scenarios where an application that is resolution-aware may want to reason on its own about the display environment it is running in.

It is important to note that the value of this property does not represent anything concrete, such as pixel density or physical size, because it can vary based on the configured display mode. For example, the display may be in a mirrored configuration that is still high-resolution scaled, resulting in pixel geometry that may not match the native resolution of the display device.

Note

For almost all common cases, developers should avoid using the value of backingScaleFactor as an input to layout or drawing calculations. Developers should instead use the backing coordinate space conversion methods, because the resulting code will more likely work consistently and correctly under both standard and high-resolution operation.

## See Also

### Converting Coordinates

func backingAlignedRect(NSRect, options: AlignmentOptions) -> NSRect

Returns a backing store pixel-aligned rectangle in window coordinates.

func convertFromBacking(NSRect) -> NSRect

Converts a rectangle from its pixel-aligned backing store coordinate system to the window’s coordinate system.

func convertFromScreen(NSRect) -> NSRect

Converts a rectangle from the screen coordinate system to the window’s coordinate system.

func convertPointFromBacking(NSPoint) -> NSPoint

Converts a point from its pixel-aligned backing store coordinate system to the window’s coordinate system.

func convertPoint(fromScreen: NSPoint) -> NSPoint

Converts a point from the screen coordinate system to the window’s coordinate system.

func convertToBacking(NSRect) -> NSRect

Converts a rectangle from the window’s coordinate system to its pixel-aligned backing store coordinate system.

func convertToScreen(NSRect) -> NSRect

Converts a rectangle to the screen coordinate system from the window’s coordinate system.

func convertPointToBacking(NSPoint) -> NSPoint

Converts a point from the window’s coordinate system to its pixel-aligned backing store coordinate system.

func convertPoint(toScreen: NSPoint) -> NSPoint

Converts a point to the screen coordinate system from the window’s coordinate system.

