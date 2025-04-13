

- Foundation
- NSString
-  draw(at:withAttributes:) 

Instance Method

# draw(at:withAttributes:)

Draws the receiver with the font and other display characteristics of the given attributes, at the specified point in the current graphics context.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func draw(
    at point: CGPoint,
    withAttributes attrs: [NSAttributedString.Key : Any]? = nil
)
```

## Parameters 

`point`  

The point in the current graphics context where you want to start drawing the string. The coordinate system of the graphics context is usually defined by the view in which you are drawing. In AppKit, the origin is normally in the lower-left corner of the drawing area, but the origin is in the upper-left corner if the focused view is flipped.

`attrs`  

A dictionary of text attributes to be applied to the string. These are the same attributes that can be applied to an NSAttributedString object, but in the case of `NSString` objects, the attributes apply to the entire string, rather than ranges within the string.

## Discussion

The width (height for vertical layout) of the rendering area is unlimited, unlike draw(in:withAttributes:), which uses a bounding rectangle. As a result, this method renders the text in a single line. However, if newline characters are present in the string, those characters are honored and cause subsequent text to be placed on the next line underneath the starting point.

There must be either a focused view or an active graphics context when you call this method.

## See Also

### Sizing and Drawing Strings

func draw(in: CGRect, withAttributes: [NSAttributedString.Key : Any]?)

Draws the attributed string inside the specified bounding rectangle.

func draw(with: CGRect, options: NSStringDrawingOptions, attributes: [NSAttributedString.Key : Any]?, context: NSStringDrawingContext?)

Draws the attributed string in the specified bounding rectangle using the provided options.

func boundingRect(with: CGSize, options: NSStringDrawingOptions, attributes: [NSAttributedString.Key : Any]?, context: NSStringDrawingContext?) -> CGRect

Calculates and returns the bounding rect for the receiver drawn using the given options and display characteristics, within the specified rectangle in the current graphics context.

func size(withAttributes: [NSAttributedString.Key : Any]?) -> CGSize

Returns the bounding box size the receiver occupies when drawn with the given attributes.

func variantFittingPresentationWidth(Int) -> String

Returns a string variation suitable for the specified presentation width.

struct NSStringDrawingOptions

Constants that specify the rendering options for drawing a string.

