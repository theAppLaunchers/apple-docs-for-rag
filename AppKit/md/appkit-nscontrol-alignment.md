

- AppKit
- NSControl
-  alignment 

Instance Property

# alignment

The alignment mode of the text in the receiver’s cell.

macOS

``` source
@MainActor
var alignment: NSTextAlignment { get set }
```

## Discussion

The value of this property can be one of the following constants: `NSLeftTextAlignment`, `NSRightTextAlignment`,`NSCenterTextAlignment`, `NSJustifiedTextAlignment`, or `NSNaturalTextAlignment`. The default value is `NSNaturalTextAlignment`. Setting this property while the cell is currently being edited aborts the edits to change the alignment.

## See Also

### Formatting Text

var font: NSFont?

The font used to draw text in the receiver’s cell.

var lineBreakMode: NSLineBreakMode

The line break mode to use for text in the control’s cell.

var usesSingleLineMode: Bool

A Boolean value that indicates whether the text in the control’s cell uses single line mode.

var formatter: Formatter?

The receiver’s formatter.

var baseWritingDirection: NSWritingDirection

The initial writing direction used to determine the actual writing direction for text.

