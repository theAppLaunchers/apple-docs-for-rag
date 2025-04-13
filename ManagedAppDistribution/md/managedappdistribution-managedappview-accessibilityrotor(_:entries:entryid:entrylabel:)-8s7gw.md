

- ManagedAppDistribution
- ManagedAppView
-  accessibilityRotor(\_:entries:entryID:entryLabel:) 

Instance Method

# accessibilityRotor(\_:entries:entryID:entryLabel:)

Create an Accessibility Rotor replacing the specified system-provided Rotor.

ManagedAppDistributionSwiftUIiOS 15.0+iPadOS 15.0+macOS 12.0+tvOS 15.0+watchOS 8.0+

``` source
nonisolated
func accessibilityRotor(
    _ systemRotor: AccessibilitySystemRotor,
    entries: [EntryModel],
    entryID: KeyPath,
    entryLabel: KeyPath
) -> some View where ID : Hashable
```

## Parameters 

`systemRotor`  

The system-provided Rotor that will be overridden by this custom Rotor.

`entries`  

An array of values that will be used to generate the entries of the Rotor.

`entryID`  

Key path on the entry type that can be used to generate an identifier for the Entry. The identifiers must match up with identifiers in `ForEach` or explicit `id` calls within the `ScrollView`.

`entryLabel`  

Key path on the entry type that can be used to get a user-visible label for every Rotor entry. This is used on macOS when the user opens the list of entries for the Rotor.

## Discussion

An Accessibility Rotor is a shortcut for Accessibility users to quickly navigate to specific elements of the user interface, and optionally specific ranges of text within those elements.

Using this modifier requires that the Rotor be attached to a `ScrollView`, or an Accessibility Element directly within a `ScrollView`, such as a `ForEach`. When the user navigates to entries from this Rotor, SwiftUI will automatically scroll them into place as needed.

In the following example, a Message application creates a Rotor allowing users to navigate to the headings in its vertical stack of messages.

```
// `messageListItems` is a list of `MessageListItem`s
// that are either a `Message` or a heading, containing a `subject`
// and a `uuid`.
// `headingMessageListItems` is a filtered list of
// `messageListItems` containing just the headings.
ScrollView {
    LazyVStack {
        ForEach(messageListItems) { messageListItem in
            switch messageListItem {
                case .heading(let subject):
                    Text(subject)
                case .message(let message):
                    MessageView(message)
            }
        }
    }
}
.accessibilityElement(children: .contain)
.accessibilityRotor(
    .heading, entries: headingMessageListItems,
    entryID: \.uuid, label: \.subject
)
```

