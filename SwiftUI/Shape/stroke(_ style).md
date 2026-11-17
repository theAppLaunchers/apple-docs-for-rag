- SwiftUI
- Shape
- stroke(_:style:)

Instance Method

# stroke(_:style:)

Traces the outline of this shape with a color or gradient.

iOS 13.0+ iPadOS 13.0+ Mac Catalyst 13.0+ macOS 10.15+ tvOS 13.0+ visionOS 1.0+ watchOS 6.0+

```swift
nonisolated
func stroke<S>(
    _ content: S,
    style: StrokeStyle
) -> some View where S : ShapeStyle
```

## Parameters

content

The color or gradient with which to stroke this shape.

style

The stroke characteristics — such as the line’s width and whether the stroke is dashed — that determine how to render this shape.

## Discussion

...

## See Also

...