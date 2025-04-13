

- SwiftUI
- Path
-  init(ellipseIn:) 

Initializer

# init(ellipseIn:)

Creates a path as an ellipse within the given rectangle.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
init(ellipseIn rect: CGRect)
```

## Parameters 

`rect`  

The rectangle that bounds the ellipse.

## Discussion

This is a convenience function that creates a path of an ellipse. Using this convenience function is more efficient than creating a path and adding an ellipse to it.

The ellipse is approximated by a sequence of Bézier curves. Its center is the midpoint of the rectangle defined by the rect parameter. If the rectangle is square, then the ellipse is circular with a radius equal to one-half the width (or height) of the rectangle. If the rect parameter specifies a rectangular shape, then the major and minor axes of the ellipse are defined by the width and height of the rectangle.

The ellipse forms a complete subpath of the path—that is, the ellipse drawing starts with a move-to operation and ends with a close-subpath operation, with all moves oriented in the clockwise direction. If you supply an affine transform, then the constructed Bézier curves that define the ellipse are transformed before they are added to the path.

## See Also

### Creating a path

init()

Creates an empty path.

init(_:)

Creates an empty path, then executes a closure to add its initial elements.

init(roundedRect: CGRect, cornerRadius: CGFloat, style: RoundedCornerStyle)

Creates a path containing a rounded rectangle.

init(roundedRect: CGRect, cornerSize: CGSize, style: RoundedCornerStyle)

Creates a path containing a rounded rectangle.

init(roundedRect: CGRect, cornerRadii: RectangleCornerRadii, style: RoundedCornerStyle)

Creates a path as the given rounded rectangle, which may have uneven corner radii.

