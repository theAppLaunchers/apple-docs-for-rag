

- RealityKit
- RealityViewContent
- RealityViewContent.Body
-  scenePadding(\_:) 

Instance Method

# scenePadding(\_:)

Adds padding to the specified edges of this view using an amount that’s appropriate for the current scene.

RealityKitSwiftUIiOS 15.0+iPadOS 15.0+macOS 12.0+tvOS 15.0+visionOSwatchOS 8.0+

``` source
nonisolated
func scenePadding(_ edges: Edge.Set = .all) -> some View
```

## Parameters 

`edges`  

The set of edges along which to pad this view.

## Return Value

A view that’s padded on specified edges by a scene-appropriate amount.

## Discussion

Use this modifier to add a scene-appropriate amount of padding to a view. Specify either a single edge value from `Edge/Set`, or an OptionSet that describes the edges to pad.

In macOS, use scene padding to produce the recommended spacing around the root view of a window. In watchOS, use scene padding to align elements of your user interface with top level elements, like the title of a navigation view. For example, compare the effects of different kinds of padding on text views presented inside a `NavigationView` in watchOS:

```
VStack(alignment: .leading, spacing: 10) {
    Text("Scene padding")
        .scenePadding(.horizontal)
        .border(.red) // Border added for reference.
    Text("Regular padding")
        .padding(.horizontal)
        .border(.green)
    Text("Text with no padding")
        .border(.blue)
    Button("Button") { }
}
.navigationTitle("Hello World")
```

The text with scene padding automatically aligns with the title, unlike the text that uses the default padding or the text without padding:

Scene padding in watchOS also ensures that your content avoids the curved edges of a device like Apple Watch Series 7. In other platforms, scene padding produces the same default padding that you get from the `View/padding(_:_:)` modifier.

Important

Scene padding doesn’t pad the top and bottom edges of a view in watchOS, even if you specify those edges as part of the input. For example, if you specify `Edge/Set/vertical` instead of `Edge/Set/horizontal` in the example above, the modifier would have no effect in watchOS. It does, however, apply to all the edges that you specify in other platforms.

