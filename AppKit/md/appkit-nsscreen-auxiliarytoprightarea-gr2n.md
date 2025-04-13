

- AppKit
- NSScreen
-  auxiliaryTopRightArea 

Instance Property

# auxiliaryTopRightArea

The unobscured portion of the top-right corner of the screen.

macOS 12.0+

``` source
var auxiliaryTopRightArea: NSRect? { get }
```

## Discussion

If the top inset of the screen’s safeAreaInsets property contains a non-zero value, the rectangle in this property is the visible top-right portion of the screen.The rectangle is specified in global screen coordinates and lies outside the safe area. If the top portion of the screen isn’t obscured, the value of this property is `nil` in Swift; in Objective-C, the value is NSZeroRect.

If your app offers a custom full-screen experience, use this property to determine what additional space is available for your custom content. The specified rectangle is safe to use to display your content.

## See Also

### Getting the Visible Portion of the Screen

var visibleFrame: NSRect

The current location and dimensions of the visible screen.

var safeAreaInsets: NSEdgeInsets

The distances from the screen’s edges at which content isn’t obscured.

var auxiliaryTopLeftArea: NSRect?

The unobscured portion of the top-left corner of the screen.

