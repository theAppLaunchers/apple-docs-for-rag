

- PencilKit
- PKToolPicker
-  PKToolPicker.Delegate 

Protocol

# PKToolPicker.Delegate

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+visionOS 2.0+

``` source
@MainActor
protocol Delegate : NSObjectProtocol
```

## Topics

### Instance Methods

func toolPickerWillDismiss(PKToolPicker) -> Bool

This is called when the user dismisses the tool picker using a built-in control. This is **not** called when the tool picker hides from a responder change or other programatic request. By default, using the dismissal control on the tool picker causes the tool picker to resign the first responder. The delegate may override that default behavior, taking responsibility for the dismissal of the picker, by returning true from this method.

## Relationships

### Inherits From

- NSObjectProtocol

