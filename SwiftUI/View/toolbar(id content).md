- SwiftUI
- View
- toolbar(id:content:)

Instance Method

# toolbar(id:content:)

Populates the toolbar or navigation bar with the specified items, allowing for user customization.

iOS 14.0+ iPadOS 14.0+ Mac Catalyst 14.0+ macOS 11.0+ tvOS 14.0+ visionOS 1.0+ watchOS 7.0+

```swift
nonisolated
func toolbar<Content>(
    id: String,
    @ContentBuilder content: () -> Content
) -> some View where Content : CustomizableToolbarContent
```

## Parameters

id

A unique identifier for this toolbar.

content

The content representing the content of the toolbar.

## Discussion

...

## See also

...