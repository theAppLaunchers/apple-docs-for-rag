

- RealityKit
- RealityViewContent
- RealityViewContent.Body
-  overlay(\_:in:fillStyle:) 

Instance Method

# overlay(\_:in:fillStyle:)

Layers a shape that you specify in front of this view.

RealityKitSwiftUIiOS 15.0+iPadOS 15.0+macOS 12.0+tvOS 15.0+visionOSwatchOS 8.0+

``` source
nonisolated
func overlay(
    _ style: S,
    in shape: T,
    fillStyle: FillStyle = FillStyle()
) -> some View where S : ShapeStyle, T : Shape
```

## Parameters 

`style`  

A `ShapeStyle` that SwiftUI uses to the fill the shape that you specify.

`shape`  

An instance of a type that conforms to `Shape` that SwiftUI draws in front of the view.

`fillStyle`  

The `FillStyle` to use when drawing the shape. The default style uses the nonzero winding number rule and antialiasing.

## Return Value

A view with the specified shape drawn in front of it.

## Discussion

Use this modifier to layer a type that conforms to the `Shape` protocol — like a `Rectangle`, `Circle`, or `Capsule` — in front of a view. Specify a `ShapeStyle` that’s used to fill the shape. For example, you can overlay the outline of one rectangle in front of another:

```
Rectangle()
    .frame(width: 200, height: 100)
    .overlay(.teal, in: Rectangle().inset(by: 10).stroke(lineWidth: 5))
```

The example above uses the `InsettableShape/inset(by:)` method to slightly reduce the size of the overlaid rectangle, and the `Shape/stroke(lineWidth:)` method to fill only the shape’s outline. This creates an inset border:

This modifier is a convenience method for layering a shape over a view. To handle the more general case of overlaying a `View` — or a stack of views — with control over the position, use `View/overlay(alignment:content:)` instead. To cover a view with a `ShapeStyle`, use `View/overlay(_:ignoresSafeAreaEdges:)`.

