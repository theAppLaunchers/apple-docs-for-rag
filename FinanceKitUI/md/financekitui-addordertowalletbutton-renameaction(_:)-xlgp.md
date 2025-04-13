

- FinanceKitUI
- AddOrderToWalletButton
-  renameAction(\_:) 

Instance Method

# renameAction(\_:)

Sets the rename action in the environment to update focus state.

FinanceKitUISwiftUIiOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+watchOS 9.0+

``` source
nonisolated
func renameAction(_ isFocused: FocusState.Binding) -> some View
```

## Parameters 

`isFocused`  

The focus binding to update when activating the rename action.

## Return Value

A view that has the specified rename action.

## Discussion

Use this modifier in conjunction with the `RenameButton` to implement standard rename interactions. A rename button receives its action from the environment. Use this modifier to customize the action provided to the rename button.

```
struct RowView: View {
    @State private var text = ""
    @FocusState private var isFocused: Bool

    var body: some View {
        TextField(text: $item.name) {
            Text("Prompt")
        }
        .focused($isFocused)
        .contextMenu {
            RenameButton()
            // ... your own custom actions
        }
        .renameAction($isFocused)
}
```

When someone taps the rename button in the context menu, the rename action focuses the text field by setting the `isFocused` property to true.

