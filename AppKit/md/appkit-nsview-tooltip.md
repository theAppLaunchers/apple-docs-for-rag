

- AppKit
- NSView
-  toolTip 

Instance Property

# toolTip

The text for the view’s tooltip.

macOS

``` source
@MainActor
var toolTip: String? { get set }
```

## Discussion

The value of this property is `nil` if the view does not currently display tooltip text. Assigning a value to this property causes the tooltip to be displayed for the view. Setting the property to nil cancels the display of the tooltip for the view.

## See Also

### Providing a Tool Tip

func addToolTip(NSRect, owner: Any, userData: UnsafeMutableRawPointer?) -> NSView.ToolTipTag

Creates a tooltip for a defined area in the view and returns a tag that identifies the tooltip rectangle.

func removeAllToolTips()

Removes all tooltips assigned to the view.

func removeToolTip(NSView.ToolTipTag)

Removes the tooltip identified by specified tag.

typealias ToolTipTag

This type describes the rectangle used to identify a tooltip rectangle.

