- SwiftUI
- View
- frame(width:height:alignment:)

Instance Method

# frame(width:height:alignment:)

Positions this view within an invisible frame with the specified size.

iOS 13.0+ iPadOS 13.0+ Mac Catalyst 13.0+ macOS 10.15+ tvOS 13.0+ visionOS 1.0+ watchOS 6.0+

```swift
nonisolated
func frame(
    width: CGFloat? = nil,
    height: CGFloat? = nil,
    alignment: Alignment = .center
) -> some View
```

## Parameters

width

A fixed width for the resulting view. If width is nil, the resulting view assumes this view’s sizing behavior.

height

A fixed height for the resulting view. If height is nil, the resulting view assumes this view’s sizing behavior.

alignment

The alignment of this view inside the resulting frame. Note that most alignment values have no apparent effect when the size of the frame happens to match that of this view.

## Return Value

A view with fixed dimensions of width and height, for the parameters that are non-nil.


## Discussion

...

## See also

...