

- FamilyControls
- FamilyActivityPicker
-  alert(\_:isPresented:presenting:actions:message:) 

Instance Method

# alert(\_:isPresented:presenting:actions:message:)

Presents an alert with a message using the given data to produce the alert’s content and a string variable as a title.

FamilyControlsSwiftUIiOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+watchOS 8.0+

``` source
nonisolated
func alert(
    _ title: S,
    isPresented: Binding,
    presenting data: T?,
    @ViewBuilder actions: (T) -> A,
    @ViewBuilder message: (T) -> M
) -> some View where S : StringProtocol, A : View, M : View
```

## Parameters 

`title`  

A text string used as the title of the alert.

`isPresented`  

A binding to a Boolean value that determines whether to present the alert. When the user presses or taps one of the alert’s actions, the system sets this value to `false` and dismisses.

`data`  

An optional source of truth for the alert. The system passes the contents to the modifier’s closures. You use this data to populate the fields of an alert that you create that the system displays to the user.

`actions`  

A `ViewBuilder` returning the alert’s actions given the currently available data.

`message`  

A `ViewBuilder` returning the message for the alert given the currently available data.

## Discussion

For the alert to appear, both `isPresented` must be `true` and `data` must not be `nil`. The data should not change after the presentation occurs. Any changes that you make after the presentation occurs are ignored.

Use this method when you need to populate the fields of an alert with content from a data source. The example below shows a custom data source, `SaveDetails`, that provides data to populate the alert:

```
struct SaveDetails: Identifiable {
    let name: String
    let error: String
    let id = UUID()
}

struct SaveButton: View {
    @State private var didError = false
    @State private var details: SaveDetails?
    let alertTitle: String = "Save failed."

    var body: some View {
        Button("Save") {
            details = model.save(didError: $didError)
        }
        .alert(
            alertTitle,
            isPresented: $didError,
            presenting: details
        ) { details in
            Button(role: .destructive) {
                // Handle the deletion.
            } label: {
                Text("Delete \(details.name)")
            }
            Button("Retry") {
                // Handle the retry action.
            }
        } message: { details in
            Text(details.error)
        }
    }
}
```

All actions in an alert dismiss the alert after the action runs. The default button is shown with greater prominence. You can influence the default button by assigning it the `KeyboardShortcut/defaultAction` keyboard shortcut.

The system may reorder the buttons based on their role and prominence.

If no actions are present, the system includes a standard “OK” action. No default cancel action is provided. If you want to show a cancel action, use a button with a role of `ButtonRole/cancel`.

On iOS, tvOS, and watchOS, alerts only support controls with labels that are `Text`. Passing any other type of view results in the content being omitted.

Only unstyled text is supported for the message.

## See Also

### Alerts with a Message

func alert&lt;A, M>(Text, isPresented: Binding&lt;Bool>, actions: () -> A, message: () -> M) -> some View

Presents an alert with a message when a given condition is true using a text view as a title.

func alert&lt;S, A, M>(S, isPresented: Binding&lt;Bool>, actions: () -> A, message: () -> M) -> some View

Presents an alert with a message when a given condition is true using a string variable as a title.

func alert&lt;A, M>(LocalizedStringKey, isPresented: Binding&lt;Bool>, actions: () -> A, message: () -> M) -> some View

Presents an alert with a message when a given condition is true, using a localized string key for a title.

func alert&lt;A, M, T>(LocalizedStringKey, isPresented: Binding&lt;Bool>, presenting: T?, actions: (T) -> A, message: (T) -> M) -> some View

Presents an alert with a message using the given data to produce the alert’s content and a localized string key for a title.

func alert&lt;A, M, T>(Text, isPresented: Binding&lt;Bool>, presenting: T?, actions: (T) -> A, message: (T) -> M) -> some View

Presents an alert with a message using the given data to produce the alert’s content and a text view for a title.

func alert&lt;E, A, M>(isPresented: Binding&lt;Bool>, error: E?, actions: (E) -> A, message: (E) -> M) -> some View

Presents an alert with a message when an error is present.

