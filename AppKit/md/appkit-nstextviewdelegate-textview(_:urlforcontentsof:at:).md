

- AppKit
- NSTextViewDelegate
-  textView(\_:urlForContentsOf:at:) 

Instance Method

# textView(\_:urlForContentsOf:at:)

Returns a URL representing the document contents for a text attachment.

macOS 10.7+

``` source
@MainActor
optional func textView(
    _ textView: NSTextView,
    urlForContentsOf textAttachment: NSTextAttachment,
    at charIndex: Int
) -> URL?
```

## Parameters 

`textView`  

The text view sending the message.

`textAttachment`  

The text attachment object containing an `NSFileWrapper` object that holds the contents of the attached file.

`charIndex`  

The character index of the text attachment.

## Return Value

The absolute URL for the document contents represented by `textAttachment`.

## Discussion

The returned `NSURL` object is used by the text view to provide default behaviors involving text attachments such as Quick Look and double-clicking. For example, the `NSTextView` method quickLookPreviewableItems(inRanges:) uses this method for mapping text attachments to their corresponding document URLs, and `NSTextView` invokes the `NSWorkspace` method open(_:) with the URL returned from this method when the delegate has no textView(_:doubleClickedOn:in:at:) implementation.

## See Also

### Related Documentation

func textView(NSTextView, doubleClickedOn: any NSTextAttachmentCellProtocol, in: NSRect, at: Int)

Sent when the user double-clicks a cell.

func quickLookPreviewableItems(inRanges: [NSValue]) -> [any QLPreviewItem]

Returns an array of URLs for items that can be displayed by QuickLook in the specified ranges.

