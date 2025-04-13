

- AppKit
- NSTextInputClient
-  attributedSubstring(forProposedRange:actualRange:) 

Instance Method

# attributedSubstring(forProposedRange:actualRange:)

Returns an attributed string derived from the given range in the receiver’s text storage.

macOS 10.0+

``` source
func attributedSubstring(
    forProposedRange range: NSRange,
    actualRange: NSRangePointer?
) -> NSAttributedString?
```

**Required**

## Parameters 

`range`  

The range in the text storage from which to create the returned string.

`actualRange`  

The actual range of the returned string if it was adjusted, for example, to a grapheme cluster boundary or for performance or other reasons. `NULL` if range was not adjusted.

## Return Value

The string created from the given range. May return `nil`.

## Discussion

An implementation of this method should be prepared for `aRange` to be out of bounds. For example, the InkWell text input service can ask for the contents of the text input client that extends beyond the document’s range. In this case, you should return the intersection of the document’s range and `aRange`. If the location of `aRange` is completely outside of the document’s range, return `nil`.

## See Also

### Storing text

func attributedString() -> NSAttributedString

Returns an attributed string representing the receiver’s text storage.

func insertText(Any, replacementRange: NSRange)

Inserts the given string into the receiver, replacing the specified content.

**Required**

