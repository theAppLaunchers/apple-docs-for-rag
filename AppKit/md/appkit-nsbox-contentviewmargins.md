

- AppKit
- NSBox
-  contentViewMargins 

Instance Property

# contentViewMargins

The distances between the border and the content view.

macOS

``` source
@MainActor
var contentViewMargins: NSSize { get set }
```

## Discussion

The width (the horizontal distance between the innermost edge of the border and the content view) and height (the vertical distance between the innermost edge of the border and the content view) describing the distance between the border and the content view. By default, these are both 5.0 in the box’s coordinate system.

Unlike changing a box’s other attributes, such as its title position or border type, changing the offsets doesn’t automatically resize the content view. In general, you should send a sizeToFit() message to the box after changing the size of its offsets. This message causes the content view to remain unchanged while the box is sized to fit around it.

## See Also

### Managing Content

var contentView: NSView?

The receiver’s content view.

