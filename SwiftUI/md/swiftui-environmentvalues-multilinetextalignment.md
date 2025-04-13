

- SwiftUI
- EnvironmentValues
-  multilineTextAlignment 

Instance Property

# multilineTextAlignment

An environment value that indicates how a text view aligns its lines when the content wraps or contains newlines.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
var multilineTextAlignment: TextAlignment { get set }
```

## Discussion

Set this value for a view hierarchy by applying the multilineTextAlignment(_:) view modifier. Views in the hierarchy that display text, like Text or TextEditor, read the value from the environment and adjust their text alignment accordingly.

This value has no effect on a Text view that contains only one line of text, because a text view has a width that exactly matches the width of its widest line. If you want to align an entire text view rather than its contents, set the aligment of its container, like a VStack or a frame that you create with the frame(minWidth:idealWidth:maxWidth:minHeight:idealHeight:maxHeight:alignment:) modifier.

Note

You can use this value to control the alignment of a Text view that you create with the init(_:style:) initializer to display localized dates and times, including when the view uses only a single line, but only when that view appears in a widget.

## See Also

### Formatting multiline text

func lineSpacing(CGFloat) -> some View

Sets the amount of space between lines of text in this view.

var lineSpacing: CGFloat

The distance in points between the bottom of one line fragment and the top of the next.

func multilineTextAlignment(TextAlignment) -> some View

Sets the alignment of a text view that contains multiple lines of text.

