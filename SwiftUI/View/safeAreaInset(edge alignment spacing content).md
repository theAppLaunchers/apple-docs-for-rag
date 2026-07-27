- SwiftUI
- View
- safeAreaInset(edge:alignment:spacing:content:)

Instance Method

# safeAreaInset(edge:alignment:spacing:content:)

Shows the specified content beside the modified view.

iOS 15.0+ iPadOS 15.0+ Mac Catalyst 15.0+ macOS 12.0+ tvOS 15.0+ visionOS 1.0+ watchOS 8.0+

```swift
nonisolated
func safeAreaInset<V>(
    edge: HorizontalEdge,
    alignment: VerticalAlignment = .center,
    spacing: CGFloat? = nil,
    @ContentBuilder content: () -> V
) -> some View where V : View
```

```swift
nonisolated
func safeAreaInset<V>(
    edge: VerticalEdge,
    alignment: HorizontalAlignment = .center,
    spacing: CGFloat? = nil,
    @ContentBuilder content: () -> V
) -> some View where V : View
```

## Parameters

edge

The horizontal edge of the view to inset by the width of content, to make space for content.

alignment

The alignment guide used to position content vertically.

spacing

Extra distance placed between the two views, or nil to use the default amount of spacing.

content

A content builder function providing the view to display in the inset space of the modified view.

## Return Value

A new view that displays content beside the modified view, making space for the content view by horizontally insetting the modified view.

## Discussion

...

## See also

...