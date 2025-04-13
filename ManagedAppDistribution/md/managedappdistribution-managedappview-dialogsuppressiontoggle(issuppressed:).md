

- ManagedAppDistribution
- ManagedAppView
-  dialogSuppressionToggle(isSuppressed:) 

Instance Method

# dialogSuppressionToggle(isSuppressed:)

Enables user suppression of dialogs and alerts presented within `self`, with a default suppression message on macOS. Unused on other platforms.

ManagedAppDistributionSwiftUIiOS 17.0+iPadOS 17.0+macOS 14.0+tvOS 17.0+watchOS 10.0+

``` source
nonisolated
func dialogSuppressionToggle(isSuppressed: Binding) -> some View
```

## Parameters 

`isSuppressed`  

Whether the suppression toggle is on or off in the dialog.

## Discussion

Applying dialog suppression adds a toggle to dialogs on macOS, which allows the user to request the alert not be displayed again. Typically whether a dialog is suppressed is stored in `AppStorage` and used to decide whether to present the dialog in the future.

The following example configures a `confirmationDialog` with a suppression toggle. The toggle’s state is stored in `AppStorage` and used to determine whether or not to show the dialog when the “Delete Items” button is pressed.

```
struct ConfirmEraseItems: View {
    @State private var isShowingDialog = false

    @AppStorage("suppressEraseItemAlert")
    private var suppressAlert = false

    var body: some View {
        Button("Delete Items") {
            if !suppressAlert {
                isShowingDialog = true
            } else {
                // Handle item deletion.
            }
        }
        .confirmationDialog(
            "Are you sure you want to erase these items?",
            isPresented: $isShowingDialog
        ) {
            Button("Erase", role: .destructive) {
                // Handle item deletion.
            }
            Button("Cancel", role: .cancel) {
                isShowingDialog = false
            }
        }
        .dialogSuppressionToggle(isSuppressed: $suppressAlert)
    }
}
```

