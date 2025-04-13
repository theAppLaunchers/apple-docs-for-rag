

- AppKit
- NSTextViewDelegate
-  textView(\_:completions:forPartialWordRange:indexOfSelectedItem:) 

Instance Method

# textView(\_:completions:forPartialWordRange:indexOfSelectedItem:)

Returns the actual completions for a partial word.

macOS

``` source
@MainActor
optional func textView(
    _ textView: NSTextView,
    completions words: [String],
    forPartialWordRange charRange: NSRange,
    indexOfSelectedItem index: UnsafeMutablePointer?
) -> [String]
```

## Parameters 

`textView`  

The text view sending the message.

`words`  

The proposed array of completions.

`charRange`  

The range of characters to be completed.

`index`  

On return, the index of the initially selected completion. The default is 0, and –1 indicates no selection.

## Return Value

The actual array of completions that will be presented for the partial word at the given range. Returning `nil` or a zero-length array suppresses completion.

