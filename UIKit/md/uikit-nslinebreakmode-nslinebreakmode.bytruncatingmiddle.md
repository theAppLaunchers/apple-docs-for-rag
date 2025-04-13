

- UIKit
- NSLineBreakMode
-  NSLineBreakMode.byTruncatingMiddle 

Case

# NSLineBreakMode.byTruncatingMiddle

The value that indicates that a line displays so that the beginning and end fit in the container and an ellipsis glyph indicates the missing text in the middle.

iOS 6.0+iPadOS 6.0+Mac Catalyst 13.1+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
case byTruncatingMiddle
```

## Discussion

Use this mode for single-line layout; using it with multiline text truncates the text into a single line.

## See Also

### Constants

case byWordWrapping

The value that indicates wrapping occurs at word boundaries, unless the word doesn’t fit on a single line.

case byCharWrapping

The value that indicates wrapping occurs before the first character that doesn’t fit.

case byClipping

The value that indicates lines don’t extend past the edge of the text container.

case byTruncatingHead

The value that indicates that a line displays so that the end fits in the container and an ellipsis glyph indicates the missing text at the beginning of the line.

case byTruncatingTail

The value that indicates a line displays so that the beginning fits in the container and an ellipsis glyph indicates the missing text at the end of the line.

