

- AppKit
- NSView
-  additionalSafeAreaInsets 

Instance Property

# additionalSafeAreaInsets

Custom insets that you specify to modify your view’s safe area

macOS 11.0+

``` source
@MainActor
var additionalSafeAreaInsets: NSEdgeInsets { get set }
```

## Discussion

Use this property to adjust the safe area insets of your view by the specified amount. The safe area defines the portion of your view’s visible area that is guaranteed to be unobscured by the bars or other ancestor-provided views.

You might use this property if your view contains content that obscures its subviews. For example, a view that draws a custom tool palette might extend the safe area to prevent subviews from displaying their content underneath the palette.

## See Also

### Respecting the View’s Safe Area

var safeAreaRect: NSRect

A rectangle in the view’s coordinate system that contains the unobscured portion of the view.

var safeAreaInsets: NSEdgeInsets

The distances from the edges of your view that define the safe area.

var safeAreaLayoutGuide: NSLayoutGuide

The layout guide you use to position content inside your view’s safe area.

