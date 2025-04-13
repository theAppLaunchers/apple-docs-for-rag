

- UIKit
- NSMutableParagraphStyle
-  maximumLineHeight 

Instance Property

# maximumLineHeight

The paragraph’s maximum line height.

iOS 6.0+iPadOS 6.0+Mac Catalyst 13.1+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var maximumLineHeight: CGFloat { get set }
```

## Discussion

This property contains the maximum height in points that any line in the receiver will occupy, regardless of the font size or size of any attached graphic. This value is always nonnegative. The default value is 0.

Glyphs and graphics exceeding this height will overlap neighboring lines; however, a maximum height of 0 implies no line height limit. Although this limit applies to the line itself, line spacing adds extra space between adjacent lines.

## See Also

### Setting style information

func setParagraphStyle(NSParagraphStyle)

Replaces the subattributes of the paragraph with those in the specified paragraph style object.

var alignment: NSTextAlignment

The text alignment of the paragraph.

var firstLineHeadIndent: CGFloat

The indentation of the first line of the paragraph.

var headIndent: CGFloat

The indentation of the paragraph’s lines other than the first.

var tailIndent: CGFloat

The trailing indentation of the paragraph.

var lineHeightMultiple: CGFloat

The line height multiple.

var minimumLineHeight: CGFloat

The paragraph’s minimum line height.

var lineSpacing: CGFloat

The distance in points between the bottom of one line fragment and the top of the next.

var paragraphSpacing: CGFloat

The space after the end of the paragraph.

var paragraphSpacingBefore: CGFloat

The distance between the paragraph’s top and the beginning of its text content.

var baseWritingDirection: NSWritingDirection

The base writing direction for the paragraph.

