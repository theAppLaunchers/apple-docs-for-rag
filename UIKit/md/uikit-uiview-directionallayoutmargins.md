

- UIKit
- UIView
-  directionalLayoutMargins 

Instance Property

# directionalLayoutMargins

The default spacing to use when laying out content in a view, taking into account the current language direction.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+tvOS 11.0+visionOS 1.0+

``` source
@MainActor
var directionalLayoutMargins: NSDirectionalEdgeInsets { get set }
```

## Mentioned in 

Positioning content within layout margins

## Discussion

Use this property to specify the desired amount of space (measured in points) between the edges of this view and its subviews. The leading and trailing margins are applied appropriately to the left or right margins based on the current layout direction. For example, the leading margin is applied to the right edge of the view in right-to-left layouts. For most views, the default layout margins are 8 points on each side. You can change these values as needed for your interface.

For the root view of a view controller, the default value of this property reflects the system minimum margins and safe area insets. For other subviews in your view hierarchy, the default layout margins are normally 8 points on each side, but the values may be greater if the view is not fully inside the safe area or if the preservesSuperviewLayoutMargins property is true.

Auto layout uses your margins as a cue for placing content. For example, if you specify a set of horizontal constraints using the format string “`|-[subview]-|`”, the leading and trailing edges of the subview are inset from the edge of the superview by the corresponding layout margins. When the edge of your view is close to the edge of the superview and the preservesSuperviewLayoutMargins property is true, the actual layout margins may be increased to prevent content from overlapping the superview’s margins.

## See Also

### Configuring content margins

Positioning content within layout margins

Position views so that they aren’t crowded by other content.

var layoutMargins: UIEdgeInsets

The default spacing to use when laying out content in the view.

var preservesSuperviewLayoutMargins: Bool

A Boolean value indicating whether the current view also respects the margins of its superview.

func layoutMarginsDidChange()

Notifies the view that the layout margins changed.

