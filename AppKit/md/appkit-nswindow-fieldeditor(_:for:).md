

- AppKit
- NSWindow
-  fieldEditor(\_:for:) 

Instance Method

# fieldEditor(\_:for:)

Returns the window’s field editor, creating it if requested.

macOS

``` source
@MainActor
func fieldEditor(
    _ createFlag: Bool,
    for object: Any?
) -> NSText?
```

## Parameters 

`createFlag`  

If true, creates a field editor if one doesn’t exist; if false, does not create a field editor.

A freshly created `NSWindow` object doesn’t have a field editor. After a field editor has been created for a window, the `createFlag` argument is ignored. By passing false for `createFlag` and testing the return value, however, you can predicate an action on the existence of the field editor.

`object`  

A text-displaying object for which the delegate (in windowWillReturnFieldEditor(_:to:)) assigns a custom field editor. Pass `nil` to get the default field editor, which can be the `NSWindow` field editor or a custom field editor returned by the delegate.

## Return Value

Returns the field editor for the designated object (`object`) or, if `object` is `nil`, the default field editor. Returns `nil` if `createFlag` is false and if the field editor doesn’t exist.

## Discussion

The field editor is a single NSTextView object that is shared among all the controls in a window for light text-editing needs. It is automatically instantiated when needed, and it can be used however your application sees fit. Typically, the field editor is used by simple text-bearing objects—for example, an NSTextField object uses its window’s field editor to display and manipulate text. The field editor can be shared by any number of objects, and so its state may be constantly changing. Therefore, it shouldn’t be used to display text that demands sophisticated layout (for this you should create a dedicated `NSTextView` object).

The field editor may be in use by some view object, so be sure to properly dissociate it from that object before actually using it yourself (the appropriate way to do this is illustrated in the description of endEditing(for:)). Once you retrieve the field editor, you can insert it in the view hierarchy, set a delegate to interpret text events, and have it perform whatever editing is needed. Then, when it sends a textDidEndEditing(_:) message to the delegate, you can get its text to display or store and remove the field editor using endEditing(for:).

The window’s delegate can substitute a custom field editor in place of the window’s field editor by implementing windowWillReturnFieldEditor(_:to:). The custom field editor can become the default editor (common to all text-displaying objects) or specific to a particular text-displaying object (`object`). The window sends this message to its delegate with itself and `object` as the arguments; if the delegate returns a non-`nil` value, the window returns that object instead of its field editor in fieldEditor(_:for:). However, note the following:

- If the window’s delegate is identical to `object`, windowWillReturnFieldEditor(_:to:) isn’t sent to the delegate.

- The object returned by the delegate method, though it may become first responder, does not become the window’s default field editor. Other objects continue to use the window’s default field editor.

## See Also

### Managing Field Editors

func endEditing(for: Any?)

Forces the field editor to give up its first responder status and prepares it for its next assignment.

