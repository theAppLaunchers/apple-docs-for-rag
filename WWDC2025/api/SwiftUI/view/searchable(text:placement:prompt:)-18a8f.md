*   [SwiftUI](/documentation/swiftui)
*   [View](/documentation/swiftui/view)
*   searchable(text:placement:prompt:)

Instance Method

# searchable(text:placement:prompt:)

Marks this view as searchable, which configures the display of a search field.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift

```swift
nonisolated
func searchable(
    text: [`Binding`](/documentation/swiftui/binding)<[`String`](/documentation/Swift/String)>,
    placement: [`SearchFieldPlacement`](/documentation/swiftui/searchfieldplacement) = .automatic,
    prompt: [`Text`](/documentation/swiftui/text)? = nil
) -> some [`View`](/documentation/swiftui/view)
```

```
```
```
```
```
```
```

```swift
```swift
Show all declarations
```
```

## [Parameters](/documentation/SwiftUI/View/searchable\(text:placement:prompt:\)-18a8f#parameters)

`text`

The text to display and edit in the search field.

`placement`

The preferred placement of the search field within the containing view hierarchy.

`prompt`

A [`Text`](/documentation/swiftui/text) view representing the prompt of the search field which provides users with guidance on what to search for.

## [Discussion](/documentation/SwiftUI/View/searchable\(text:placement:prompt:\)-18a8f#discussion)

For more information about using searchable modifiers, see [Adding a search interface to your app](/documentation/swiftui/adding-a-search-interface-to-your-app).