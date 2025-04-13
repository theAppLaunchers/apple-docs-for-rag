

- SwiftUI
- ScrollDismissesKeyboardMode
-  automatic 

Type Property

# automatic

Determine the mode automatically based on the surrounding context.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+watchOS 9.0+

``` source
static var automatic: ScrollDismissesKeyboardMode { get }
```

## Discussion

By default, a TextEditor is interactive while a List of scrollable content always dismiss the keyboard on a scroll, when linked against iOS 16 or later.

## See Also

### Getting modes

static var immediately: ScrollDismissesKeyboardMode

Dismiss the keyboard as soon as scrolling starts.

static var interactively: ScrollDismissesKeyboardMode

Enable people to interactively dismiss the keyboard as part of the scroll operation.

static var never: ScrollDismissesKeyboardMode

Never dismiss the keyboard automatically as a result of scrolling.

