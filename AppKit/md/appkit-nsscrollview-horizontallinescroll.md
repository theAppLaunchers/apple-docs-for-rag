

- AppKit
- NSScrollView
-  horizontalLineScroll 

Instance Property

# horizontalLineScroll

The scroll view’s horizontal line by line scroll amount.

macOS

``` source
@MainActor
var horizontalLineScroll: CGFloat { get set }
```

## Discussion

The value of this property is the amount by which the scroll view scrolls itself horizontally when scrolling line by line, expressed in the content view’s coordinate system. This value is used when the user clicks the scroll arrows on the horizontal scroll bar without holding down a modifier key.

## See Also

### Setting Scrolling Behavior

var lineScroll: CGFloat

The scroll view’s line by line scroll amount.

var verticalLineScroll: CGFloat

The scroll view’s vertical line by line scroll amount.

var pageScroll: CGFloat

The amount of the document view kept visible when scrolling page by page.

var horizontalPageScroll: CGFloat

The amount of the document view kept visible when scrolling horizontally page by page.

var verticalPageScroll: CGFloat

The amount of the document view kept visible when scrolling vertically page by page.

var scrollsDynamically: Bool

A Boolean that indicates whether the scroll view redraws its document view while scrolling continuously.

func scrollWheel(with: NSEvent)

Scrolls the receiver up or down, in response to the user moving the mouse’s scroll wheel specified by `theEvent`.

