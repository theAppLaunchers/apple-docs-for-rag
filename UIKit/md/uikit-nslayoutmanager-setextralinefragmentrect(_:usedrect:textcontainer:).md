

- UIKit
- NSLayoutManager
-  setExtraLineFragmentRect(\_:usedRect:textContainer:) 

Instance Method

# setExtraLineFragmentRect(\_:usedRect:textContainer:)

Sets the bounds and container for the extra line fragment.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+tvOSvisionOS 1.0+

``` source
func setExtraLineFragmentRect(
    _ fragmentRect: CGRect,
    usedRect: CGRect,
    textContainer container: NSTextContainer
)
```

## Parameters 

`fragmentRect`  

The rectangle to set.

`usedRect`  

Indicates where the insertion point is drawn.

`container`  

The text container where the rectangle is to be laid out.

## Discussion

The extra line fragment is used when the text backing ends with a hard line break or when the text backing is totally empty, to define the extra line which needs to be displayed at the end of the text. If the text backing is not empty and does not end with a hard line break, this should be set to NSZeroRect and `nil`.

Line fragment rectangles and line fragment used rectangles are always in container coordinates.

This method is used by the layout mechanism and should be invoked only during typesetting, in almost all cases only by the typesetter. For example, a custom typesetter might invoke it.

## See Also

### Setting layout information

func setAttachmentSize(CGSize, forGlyphRange: NSRange)

Sets the size to use when drawing a glyph that represents an attachment.

func setDrawsOutsideLineFragment(Bool, forGlyphAt: Int)

Indicates whether the specified glyph exceeds the bounds of the line fragment for its layout.

func setLineFragmentRect(CGRect, forGlyphRange: NSRange, usedRect: CGRect)

Associates the line fragment bounds for the specified range of glyphs.

func setLocation(CGPoint, forStartOfGlyphRange: NSRange)

Sets the location for the first glyph in the specified range.

func setNotShownAttribute(Bool, forGlyphAt: Int)

Sets the visibility of the glyph at the specified index.

