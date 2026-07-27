- SwiftUI
- View
- alert(_:isPresented:actions:)

Instance Method

# alert(_:isPresented:actions:)

Presents an alert when a given condition is true, using a string variable as a title.

iOS 15.0+ iPadOS 15.0+ Mac Catalyst 15.0+ macOS 12.0+ tvOS 15.0+ visionOS 1.0+ watchOS 8.0+

```swift
@export(implementation) nonisolated
func alert<A>(
    _ titleResource: LocalizedStringResource,
    isPresented: Binding<Bool>,
    @ContentBuilder actions: () -> A
) -> some View where A : View
```

```swift
nonisolated
func alert<A>(
    _ title: Text,
    isPresented: Binding<Bool>,
    @ContentBuilder actions: () -> A
) -> some View where A : View
```

```swift
nonisolated
func alert<A>(
    _ titleKey: LocalizedStringKey,
    isPresented: Binding<Bool>,
    @ContentBuilder actions: () -> A
) -> some View where A : View
```

```swift
nonisolated
func alert<S, A>(
    _ title: S,
    isPresented: Binding<Bool>,
    @ContentBuilder actions: () -> A
) -> some View where S : StringProtocol, A : View
```

## Parameters

title

A text string used as the title of the alert.

isPresented

A binding to a Boolean value that determines whether to present the alert. When the user presses or taps one of the alert’s actions, the system sets this value to false and dismisses.

actions

A ContentBuilder returning the alert’s actions.

## Discussion

...

## See also

...