- SwiftUI
- View
- containerRelativeFrame(_:alignment:_:)

Instance Method

# containerRelativeFrame(_:alignment:_:)

Positions this view within an invisible frame with a size relative to the nearest container.

iOS 17.0+ iPadOS 17.0+ Mac Catalyst 17.0+ macOS 14.0+ tvOS 17.0+ visionOS 1.0+ watchOS 10.0+

```swift
nonisolated
func containerRelativeFrame(
    _ axes: Axis.Set,
    alignment: Alignment = .center,
    _ length: @escaping (CGFloat, Axis) -> CGFloat
) -> some View
```

## Discussion

...

## See also

...