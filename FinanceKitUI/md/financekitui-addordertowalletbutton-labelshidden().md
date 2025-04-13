

- FinanceKitUI
- AddOrderToWalletButton
-  labelsHidden() 

Instance Method

# labelsHidden()

Hides the labels of any controls contained within this view.

FinanceKitUISwiftUIiOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+watchOS 6.0+

``` source
nonisolated
func labelsHidden() -> some View
```

## Discussion

Use this modifier when you want to omit a label from one or more controls in your user interface. For example, the first `Toggle` in the following example hides its label:

```
VStack {
    Toggle(isOn: $toggle1) {
        Text("Toggle 1")
    }
    .labelsHidden()

    Toggle(isOn: $toggle2) {
        Text("Toggle 2")
    }
}
```

The `VStack` in the example above centers the first toggle’s control element in the available space, while it centers the second toggle’s combined label and control element:

Always provide a label for controls, even when you hide the label, because SwiftUI uses labels for other purposes, including accessibility.

Note

This modifier doesn’t work for all labels. It applies to labels that are separate from the rest of the control’s interface, like they are for `Toggle`, but not to controls like a bordered button where the label is inside the button’s border.

