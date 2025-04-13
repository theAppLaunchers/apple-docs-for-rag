

- Assignables
- AssignedWorkDocumentView
-  interactiveDismissDisabled(\_:) 

Instance Method

# interactiveDismissDisabled(\_:)

Conditionally prevents interactive dismissal of presentations like popovers, sheets, and inspectors.

AssignablesSwiftUIiOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOSwatchOS 8.0+

``` source
nonisolated
func interactiveDismissDisabled(_ isDisabled: Bool = true) -> some View
```

## Parameters 

`isDisabled`  

A Boolean value that indicates whether to prevent nonprogrammatic dismissal of the containing view hierarchy when presented in a sheet or popover.

## Discussion

Users can dismiss certain kinds of presentations using built-in gestures. In particular, a user can dismiss a sheet by dragging it down, or a popover by clicking or tapping outside of the presented view. Use the `interactiveDismissDisabled(_:)` modifier to conditionally prevent this kind of dismissal. You typically do this to prevent the user from dismissing a presentation before providing needed data or completing a required action.

For instance, suppose you have a view that displays a licensing agreement that the user must acknowledge before continuing:

```
struct TermsOfService: View {
    @Binding var areTermsAccepted: Bool
    @Environment(\.dismiss) private var dismiss

    var body: some View {
        Form {
            Text("License Agreement")
                .font(.title)
            Text("Terms and conditions go here.")
            Button("Accept") {
                areTermsAccepted = true
                dismiss()
            }
        }
    }
}
```

If you present this view in a sheet, the user can dismiss it by either tapping the button — which calls `EnvironmentValues/dismiss` from its `action` closure — or by dragging the sheet down. To ensure that the user accepts the terms by tapping the button, disable interactive dismissal, conditioned on the `areTermsAccepted` property:

```
struct ContentView: View {
    @State private var isSheetPresented = false
    @State private var areTermsAccepted = false

    var body: some View {
        Button("Use Service") {
            isSheetPresented = true
        }
        .sheet(isPresented: $isSheetPresented) {
            TermsOfService()
                .interactiveDismissDisabled(!areTermsAccepted)
        }
    }
}
```

You can apply the modifier to any view in the sheet’s view hierarchy, including to the sheet’s top level view, as the example demonstrates, or to any child view, like the `Form` or the Accept `Button`.

The modifier has no effect on programmatic dismissal, which you can invoke by updating the `Binding` that controls the presentation, or by calling the environment’s `EnvironmentValues/dismiss` action. On macOS, disabling interactive dismissal in a popover makes the popover nontransient.

