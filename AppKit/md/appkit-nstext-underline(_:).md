

- AppKit
- NSText
-  underline(\_:) 

Instance Method

# underline(\_:)

Adds the underline attribute to the selected text attributes if absent; removes the attribute if present.

macOS

``` source
@MainActor
func underline(_ sender: Any?)
```

## Discussion

If there is a selection and the first character of the selected range has any form of underline on it, or if there is no selection and the typing attributes have any form of underline, then underline is removed; otherwise a single simple underline is added.

Operates on the selected range if the receiver contains rich text. For plain text the range is the entire contents of the receiver.

