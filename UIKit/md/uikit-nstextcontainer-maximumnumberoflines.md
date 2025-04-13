

- UIKit
- NSTextContainer
-  maximumNumberOfLines 

Instance Property

# maximumNumberOfLines

The maximum number of lines that the text container can store.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+tvOS 9.0+visionOS 1.0+

``` source
var maximumNumberOfLines: Int { get set }
```

## Discussion

The layout manager uses the value of this property to determine the maximum number of lines associated with the text container. The default value of this property is `0`, which indicates that there is no limit.

## See Also

### Constraining text layout

var lineFragmentPadding: CGFloat

The value for the text inset within line fragment rectangles.

func lineFragmentRect(forProposedRect: CGRect, at: Int, writingDirection: NSWritingDirection, remaining: UnsafeMutablePointer&lt;CGRect>?) -> CGRect

Returns the bounds of a line fragment rectangle inside the text container for the proposed rectangle.

var isSimpleRectangularTextContainer: Bool

A Boolean that indicates whether the text container’s region is a rectangle with no holes or gaps, and whose edges are parallel to the text view’s coordinate system axes.

