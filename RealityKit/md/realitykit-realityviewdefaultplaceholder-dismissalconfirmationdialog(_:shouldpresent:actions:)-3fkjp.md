

- RealityKit
- RealityViewDefaultPlaceholder
-  dismissalConfirmationDialog(\_:shouldPresent:actions:) 

Instance Method

# dismissalConfirmationDialog(\_:shouldPresent:actions:)

Presents a confirmation dialog when a dismiss action has been triggered.

RealityKitSwiftUImacOS 15.0+

``` source
nonisolated
func dismissalConfirmationDialog(
    _ title: S,
    shouldPresent: Bool,
    @ViewBuilder actions: () -> A
) -> some View where S : StringProtocol, A : View
```

## Parameters 

`title`  

A text string used as the title of the dialog.

`shouldPresent`  

A a Boolean value that determines whether to present the dialog upon dismissal.

`actions`  

A view builder returning the dialog’s actions.

## Discussion

On macOS, the dialog will be presented when attempting to dismiss the window for this view.

For example, you could present a dialog asking to persist unsaved changes:

struct ComposeMessage: View { @State private var message = Message()

```
var body: some View {
    MessageEditor(message: $message)
        .dismissalConfirmationDialog(
            "Save This Message As Draft?",
            shouldPresent: message.hasUnsavedChanges
        ) {
            Button("Save") {
                message.save()
            }
            Button("Don't Save", role: .destructive) {
                message.discard()
            }
        } message: {
            Text(
                """
                This message has not been sent and contains\
                unsaved changes.
                """)
        }
```

}

All actions in the dialog will dismiss the dialog after the action runs. The default button will be shown with greater prominence. You can influence the default button by assigning it the `KeyboardShortcut/defaultAction` keyboard shortcut.

The system may reorder the buttons based on their role and prominence.

Dismissal dialogs include a standard cancellation action by default. If you provide a button with a role of `ButtonRole/cancel`, that button takes the place of the default cancellation action.

The cancellation action will always prevent the dismissal, while other actions will allow the dismiss to proceed.

