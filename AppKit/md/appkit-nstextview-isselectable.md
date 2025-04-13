

- AppKit
- NSTextView
-  isSelectable 

Instance Property

# isSelectable

A Boolean value that controls whether the text views sharing the receiver’s layout manager allow the user to select text.

macOS

``` source
@MainActor
var isSelectable: Bool { get set }
```

## Discussion

true to allow the user to select text of all text views sharing the receiver’s layout manager; otherwise, false.

If a text view is made not selectable, it’s also made not editable, and buttons on the Find panel are dimmed. Text views are by default both editable and selectable

Note

Non-selectable text views do not process any mouse events. If for some reason it is necessary to disallow user selection changes in a text view that must handle mouse events, you can make the text view selectable but implement the delegate method textView(_:willChangeSelectionFromCharacterRanges:toCharacterRanges:) to disallow selection changes.

## See Also

### Setting behavioral attributes

var allowsUndo: Bool

A Boolean value that indicates whether the receiver allows undo.

var isEditable: Bool

A Boolean value that controls whether the text views sharing the receiver’s layout manager allow the user to edit text.

var isFieldEditor: Bool

A Boolean value that controls whether the text views sharing the receiver’s layout manager behave as field editors.

var isRichText: Bool

A Boolean value that controls whether the text views sharing the receiver’s layout manager allow the user to apply attributes to specific ranges of text.

var importsGraphics: Bool

A Boolean value that controls whether the text views sharing the receiver’s layout manager allow the user to import files by dragging.

func setBaseWritingDirection(NSWritingDirection, range: NSRange)

Sets the base writing direction of a range of text.

var defaultParagraphStyle: NSParagraphStyle?

The receiver’s default paragraph style.

func outline(Any?)

Adds the outline attribute to the selected text attributes if absent; removes the attribute if present.

var allowsImageEditing: Bool

Indicates whether image attachments should permit editing of their images.

var isAutomaticQuoteSubstitutionEnabled: Bool

A Boolean value that enables and disables automatic quotation mark substitution.

func toggleAutomaticQuoteSubstitution(Any?)

Changes the state of automatic quotation mark substitution from enabled to disabled and vice versa.

var isAutomaticLinkDetectionEnabled: Bool

A Boolean value that enables or disables automatic link detection.

func toggleAutomaticLinkDetection(Any?)

Changes the state of automatic link detection from enabled to disabled and vice versa.

var displaysLinkToolTips: Bool

A Boolean value that indicates whether the text view automatically supplies the destination of a link as a tooltip for text that has a link attribute.

var isAutomaticTextCompletionEnabled: Bool

A Boolean value that indicates whether the text view supplies autocompletion suggestions as the user types.

