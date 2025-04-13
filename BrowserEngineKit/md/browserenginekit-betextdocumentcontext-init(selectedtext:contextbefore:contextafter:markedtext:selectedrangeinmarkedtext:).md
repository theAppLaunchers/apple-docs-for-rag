

- BrowserEngineKit
- BETextDocumentContext
-  init(selectedText:contextBefore:contextAfter:markedText:selectedRangeInMarkedText:) 

Initializer

# init(selectedText:contextBefore:contextAfter:markedText:selectedRangeInMarkedText:)

iOS 17.4+iPadOS 17.4+tvOS 17.4+visionOS 1.1+

``` source
init(
    selectedText: String?,
    contextBefore: String?,
    contextAfter: String?,
    markedText: String?,
    selectedRangeInMarkedText: NSRange
)
```

## Parameters 

`contextBefore`  

A suffix of the text preceding the selection, or nil if the selection is at the beginning of the document. This text must correspond to a range that does not include any non-text content. In particular, if a context comprises k backward-deletion clusters, then k calls to -deleteBackward must delete the corresponding text from the document. The beginning of this string must lie on a word boundary (or not be inside a word at all).

`contextAfter`  

A prefix of the text following the selection, or nil if the selection is at the end of the document. This text must correspond to a range that does not include any non-text content. The end of this string must lie on a word boundary (or not be inside a word at all).

`markedText`  

May be empty if it’s outside of the context’s area, even if it exists elsewhere in the document.

`selectedRangeInMarkedText`  

The range of the current text selection, relative to the marked text range. Specify (NSNotFound, 0) if there is no marked text.

## Discussion

This string may be empty but non-nil if non-textual content is selected, in which case a single call to -deleteBackward will not delete from contextBeforeSelection. May be empty if its outside of the context’s area, even if it exists elsewhere in the document.

## See Also

### Creating a text document context

init(attributedSelectedText: NSAttributedString?, contextBefore: NSAttributedString?, contextAfter: NSAttributedString?, markedText: NSAttributedString?, selectedRangeInMarkedText: NSRange)

Initializes a new document context with attributed strings. The `selectedText`, `contextBefore`, and `contextAfter` represent the same ranges as they do in the `-initWithSelectedText:contextBefore:contextAfter:` initializer.

