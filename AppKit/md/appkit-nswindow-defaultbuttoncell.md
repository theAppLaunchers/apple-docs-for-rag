

- AppKit
- NSWindow
-  defaultButtonCell 

Instance Property

# defaultButtonCell

The button cell that performs as if clicked when the window receives a Return (or Enter) key event.

macOS

``` source
@MainActor
var defaultButtonCell: NSButtonCell? { get set }
```

## Discussion

This cell draws itself as the focal element for keyboard interface control, unless another button cell is focused on, in which case the default button cell temporarily draws itself as normal and disables its key equivalent.

The window receives a Return key event if no responder in its responder chain claims it, or if the user presses the Control key along with the Return key.

## See Also

### Managing Default Buttons

func enableKeyEquivalentForDefaultButtonCell()

Reenables the default button cell’s key equivalent, so it performs a click when the user presses Return (or Enter).

func disableKeyEquivalentForDefaultButtonCell()

Disables the default button cell’s key equivalent, so it doesn’t perform a click when the user presses Return (or Enter).

