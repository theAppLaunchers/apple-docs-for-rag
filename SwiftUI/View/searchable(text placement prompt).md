- SwiftUI
- View
- searchable(text:placement:prompt:)

Instance Method

# searchable(text:placement:prompt:)

Marks this view as searchable, which configures the display of a search field.

iOS 16.0+ iPadOS 16.0+ Mac Catalyst 16.0+ macOS 13.0+ tvOS 16.0+ visionOS 1.0+ watchOS 9.0+

```swift
@export(implementation) nonisolated
func searchable(
    text: Binding<String>,
    placement: SearchFieldPlacement = .automatic,
    prompt: LocalizedStringResource
) -> some View
```

```swift
nonisolated
func searchable(
    text: Binding<String>,
    placement: SearchFieldPlacement = .automatic,
    prompt: LocalizedStringKey
) -> some View
```

```swift
nonisolated
func searchable(
    text: Binding<String>,
    placement: SearchFieldPlacement = .automatic,
    prompt: Text? = nil
) -> some View
```

```swift
nonisolated
func searchable<S>(
    text: Binding<String>,
    placement: SearchFieldPlacement = .automatic,
    prompt: S
) -> some View where S : StringProtocol
```

## Parameters

text

The text to display and edit in the search field.

placement

The preferred placement of the search field within the containing view hierarchy.

prompt

A string representing the prompt of the search field which provides users with guidance on what to search for.

## Return Value

A new view that displays content beside the modified view, making space for the content view by horizontally insetting the modified view.

## Discussion

...