- SwiftUI
- View
- overlay(alignment:content:)

Instance Method

# overlay(alignment:content:)

Layers the views that you specify in front of this view.

iOS 15.0+ iPadOS 15.0+ Mac Catalyst 15.0+ macOS 12.0+ tvOS 15.0+ visionOS 1.0+ watchOS 8.0+

```swift
nonisolated
func overlay<V>(
    alignment: Alignment = .center,
    @ContentBuilder content: () -> V
) -> some View where V : View
```

## Parameters

alignment

The alignment that the modifier uses to position the implicit ZStack that groups the foreground views. The default is center.

content

A ContentBuilder that you use to declare the views to draw in front of this view, stacked in the order that you list them. The last view that you list appears at the front of the stack.

## Return Value

A view that uses the specified content as a foreground.

## Discussion

...

## See also

...