

- AppKit
- NSControlTextEditingDelegate
-  control(\_:textView:doCommandBy:) 

Instance Method

# control(\_:textView:doCommandBy:)

Invoked when users press keys with predefined bindings in a cell of the specified control.

macOS 10.0+

``` source
@MainActor
optional func control(
    _ control: NSControl,
    textView: NSTextView,
    doCommandBy commandSelector: Selector
) -> Bool
```

## Parameters 

`control`  

The control whose cell initiated the message. If the control contains multiple cells, the one that initiated the message is usually the selected cell.

`textView`  

The field editor of the control.

`commandSelector`  

The selector that was associated with the binding.

## Return Value

true if the delegate object handles the key binding; otherwise, false.

## Discussion

These bindings are usually implemented as methods (`command`) defined in the `NSResponder` class; examples of such key bindings are arrow keys (for directional movement) and the Escape key (for name completion). By implementing this method, the delegate can override the default implementation of `command` and supply its own behavior.

For example, the default method for completing partially typed pathnames or symbols (usually when users press the Escape key) is `complete(_:)`. The default implementation of the `complete(_:)` method (in `NSResponder`) does nothing. The delegate could evaluate the method in the `command` parameter and, if it’s `complete(_:)`, get the current string from the `textView` parameter and then expand it, or display a list of potential completions, or do whatever else is appropriate.

