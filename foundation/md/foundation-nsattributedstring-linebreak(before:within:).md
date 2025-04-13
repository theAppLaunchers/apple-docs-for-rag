

- Foundation
- NSAttributedString
-  lineBreak(before:within:) 

Instance Method

# lineBreak(before:within:)

Returns the appropriate line break when the character at the index doesn’t fit on the same line as the character at the beginning of the range.

macOS 10.0+

``` source
func lineBreak(
    before location: Int,
    within aRange: NSRange
) -> Int
```

## Parameters 

`location`  

The index in the attributed string.

`aRange`  

The range.

## Return Value

Returns the index of the closest character before `index` within `aRange`, that can be placed on a new line when laying out text. Returns `NSNotFound` if no line break is possible before `index`.

## Discussion

Raises an rangeException if `index` or any part of `aRange` lies beyond the end of the receiver’s characters.

## See Also

### Calculating linguistic units

func doubleClick(at: Int) -> NSRange

Returns the range of characters that form a word (or other linguistic unit) surrounding the specified index, taking language characteristics into account.

func lineBreakByHyphenating(before: Int, within: NSRange) -> Int

Returns the index of the closest character before the specified index, and within the specified range, that can fit on a new line by hyphenating.

func nextWord(from: Int, forward: Bool) -> Int

Returns the index of the first character of the word after or before the specified index.

