- SwiftUI
- View
- confirmationDialog(_:isPresented:titleVisibility:actions:)

Instance Method

# confirmationDialog(_:isPresented:titleVisibility:actions:)

Presents a confirmation dialog when a given condition is true, using a string variable as a title.

iOS 15.0+ iPadOS 15.0+ Mac Catalyst 15.0+ macOS 12.0+ tvOS 15.0+ visionOS 1.0+ watchOS 8.0+

```swift
@export(implementation) nonisolated
func confirmationDialog<A>(
    _ titleResource: LocalizedStringResource,
    isPresented: Binding<Bool>,
    titleVisibility: Visibility = .automatic,
    @ContentBuilder actions: () -> A
) -> some View where A : View
```

```swift
nonisolated
func confirmationDialog<A>(
    _ title: Text,
    isPresented: Binding<Bool>,
    titleVisibility: Visibility = .automatic,
    @ContentBuilder actions: () -> A
) -> some View where A : View
```

```swift
nonisolated
func confirmationDialog<A>(
    _ titleKey: LocalizedStringKey,
    isPresented: Binding<Bool>,
    titleVisibility: Visibility = .automatic,
    @ContentBuilder actions: () -> A
) -> some View where A : View
```

```swift
nonisolated
func confirmationDialog<S, A>(
    _ title: S,
    isPresented: Binding<Bool>,
    titleVisibility: Visibility = .automatic,
    @ContentBuilder actions: () -> A
) -> some View where S : StringProtocol, A : View
```

## Parameters

title

A text string used as the title of the dialog.

isPresented

A binding to a Boolean value that determines whether to present the dialog. When the user presses or taps the dialog’s default action button, the system sets this value to false, dismissing the dialog.

titleVisibility

The visibility of the dialog’s title. The default value is Visibility.automatic.

actions

A ContentBuilder returning the dialog’s actions.


## Discussion

...

## See also

...