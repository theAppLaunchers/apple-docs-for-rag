- SwiftUI
- View
- background(alignment:content:)

Instance Method

# background(alignment:content:)

Layers the views that you specify behind this view.

iOS 15.0+ iPadOS 15.0+ Mac Catalyst 15.0+ macOS 12.0+ tvOS 15.0+ visionOS 1.0+ watchOS 8.0+

```swift
nonisolated
func background<V>(
    alignment: Alignment = .center,
    @ContentBuilder content: () -> V
) -> some View where V : View
```

## Parameters

alignment

The alignment that the modifier uses to position the implicit ZStack that groups the background views. The default is center.

content

A ContentBuilder that you use to declare the views to draw behind this view, stacked in a cascading order from bottom to top. The last view that you list appears at the front of the stack.

## Return Value

A view that uses the specified content as a background.

## Discussion

...

## See also

...