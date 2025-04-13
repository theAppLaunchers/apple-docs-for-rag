

- RealityKit
- RealityView
-  frame(width:height:alignment:) 

Instance Method

# frame(width:height:alignment:)

Positions this view within an invisible frame with the specified size.

RealityKitSwiftUIiOS 13.0+iPadOS 13.0+Mac CatalystmacOS 10.15+tvOS 13.0+visionOSwatchOS 6.0+

``` source
nonisolated
func frame(
    width: CGFloat? = nil,
    height: CGFloat? = nil,
    alignment: Alignment = .center
) -> some View
```

## Parameters 

`width`  

A fixed width for the resulting view. If `width` is `nil`, the resulting view assumes this view’s sizing behavior.

`height`  

A fixed height for the resulting view. If `height` is `nil`, the resulting view assumes this view’s sizing behavior.

`alignment`  

The alignment of this view inside the resulting frame. Note that most alignment values have no apparent effect when the size of the frame happens to match that of this view.

## Return Value

A view with fixed dimensions of `width` and `height`, for the parameters that are non-`nil`.

## Discussion

Use this method to specify a fixed size for a view’s width, height, or both. If you only specify one of the dimensions, the resulting view assumes this view’s sizing behavior in the other dimension.

For example, the following code lays out an ellipse in a fixed 200 by 100 frame. Because a shape always occupies the space offered to it by the layout system, the first ellipse is 200x100 points. The second ellipse is laid out in a frame with only a fixed height, so it occupies that height, and whatever width the layout system offers to its parent.

```
VStack {
    Ellipse()
        .fill(Color.purple)
        .frame(width: 200, height: 100)
    Ellipse()
        .fill(Color.blue)
        .frame(height: 100)
}
```

`The alignment` parameter specifies this view’s alignment within the frame.

```
Text("Hello world!")
    .frame(width: 200, height: 30, alignment: .topLeading)
    .border(Color.gray)
```

In the example above, the text is positioned at the top, leading corner of the frame. If the text is taller than the frame, its bounds may extend beyond the bottom of the frame’s bounds.

