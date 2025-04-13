

- RealityKit
- RealityViewContent
- RealityViewContent.Body
-  alignmentGuide(\_:computeValue:) 

Instance Method

# alignmentGuide(\_:computeValue:)

Sets the view’s vertical alignment.

RealityKitSwiftUIiOS 13.0+iPadOS 13.0+macOS 10.15+tvOS 13.0+visionOSwatchOS 6.0+

``` source
@preconcurrency nonisolated
func alignmentGuide(
    _ g: VerticalAlignment,
    computeValue: @escaping (ViewDimensions) -> CGFloat
) -> some View
```

## Parameters 

`g`  

A `VerticalAlignment` value at which to base the offset.

`computeValue`  

A closure that returns the offset value to apply to this view.

## Return Value

A view modified with respect to its vertical alignment according to the computation performed in the method’s closure.

## Discussion

Use `alignmentGuide(_:computeValue:)` to calculate specific offsets to reposition views in relationship to one another. You can return a constant or can use the `ViewDimensions` argument to the closure to calculate a return value.

In the example below, the weather emoji are offset 20 points from the vertical center of the `HStack`.

```
VStack {
    Text("Today's Weather")
        .font(.title)
        .border(.gray)

    HStack {
        Text("🌧")
            .alignmentGuide(VerticalAlignment.center) { _ in -20 }
            .border(.gray)
        Text("Rain & Thunderstorms")
            .border(.gray)
        Text("⛈")
            .alignmentGuide(VerticalAlignment.center) { _ in 20 }
            .border(.gray)
    }
}
```

Changing the alignment of one view may have effects on surrounding views. Here the offset values inside a stack and its contained views is the difference of their absolute offsets.

