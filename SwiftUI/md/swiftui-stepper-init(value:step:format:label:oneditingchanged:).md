

- SwiftUI
- Stepper
-  init(value:step:format:label:onEditingChanged:) 

Initializer

# init(value:step:format:label:onEditingChanged:)

Creates a stepper configured to increment or decrement a binding to a value using a step value you provide, displaying its value with an applied format style.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+visionOS 1.0+watchOS 9.0+

``` source
nonisolated
init(
    value: Binding,
    step: F.FormatInput.Stride = 1,
    format: F,
    @ViewBuilder label: () -> Label,
    onEditingChanged: @escaping (Bool) -> Void = { _ in }
) where F : ParseableFormatStyle, F.FormatInput : BinaryFloatingPoint, F.FormatOutput == String
```

Available when `Label` conforms to `View`.

## Parameters 

`value`  

The Binding to a value that you provide.

`step`  

The amount to increment or decrement `value` each time the user clicks or taps the stepper’s increment or decrement buttons. Defaults to `1`.

`format`  

A format style of type `F` to use when converting between the string the user edits and the underlying value of type `F.FormatInput`. If `format` can’t perform the conversion, the stepper leaves `value` unchanged. If the user stops editing the text in an invalid state, the stepper updates the text to the last known valid value.

`label`  

A view describing the purpose of this stepper.

`onEditingChanged`  

A closure that’s called when editing begins and ends. For example, on iOS, the user may touch and hold the increment or decrement buttons on a stepper which causes the execution of the `onEditingChanged` closure at the start and end of the gesture.

## Discussion

Use this initializer to create a stepper that increments or decrements a bound value by a specific amount each time the user clicks or taps the stepper’s increment or decrement buttons, while displaying the current value.

In the example below, a stepper increments or decrements `value` by the `step` value of 5 at each click or tap of the control’s increment or decrement button:

```
struct StepperView: View {
    @State private var value = 1
    let step = 5
    var body: some View {
        Stepper(value: $value,
                step: step,
                format: .number) {
            Text("Current value: \(value), step: \(step)")
        }
            .padding(10)
    }
}
```

## See Also

### Creating a stepper

init&lt;V>(value: Binding&lt;V>, step: V.Stride, label: () -> Label, onEditingChanged: (Bool) -> Void)

Creates a stepper configured to increment or decrement a binding to a value using a step value you provide.

init(_:value:step:onEditingChanged:)

Creates a stepper with a title and configured to increment and decrement a binding to a value and step amount you provide.

init(_:value:step:format:onEditingChanged:)

Creates a stepper with a title key and configured to increment and decrement a binding to a value and step amount you provide, displaying its value with an applied format style.

