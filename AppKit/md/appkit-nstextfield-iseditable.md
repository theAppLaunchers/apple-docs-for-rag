

- AppKit
- NSTextField
-  isEditable 

Instance Property

# isEditable

A Boolean value that controls whether the user can edit the value in the text field.

macOS

``` source
@MainActor
var isEditable: Bool { get set }
```

## Discussion

If true, the user can select and edit text. If false, the user can’t edit text, and the ability to select the text field’s content is dependent on the value of isSelectable.

For example, if an `NSTextField` object is selectable but uneditable, becomes editable for a time, and then becomes uneditable again, it remains selectable. To ensure that text is neither editable nor selectable, use isSelectable to disable text selection.

## See Also

### Controlling Selection and Editing

var isSelectable: Bool

A Boolean value that determines whether the user can select the content of the text field.

