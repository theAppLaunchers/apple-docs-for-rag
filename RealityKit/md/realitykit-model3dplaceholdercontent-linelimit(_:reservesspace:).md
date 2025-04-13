

- RealityKit
- Model3DPlaceholderContent
-  lineLimit(\_:reservesSpace:) 

Instance Method

# lineLimit(\_:reservesSpace:)

Sets a limit for the number of lines text can occupy in this view.

RealityKitSwiftUIiOS 16.0+iPadOS 16.0+macOS 13.0+tvOS 16.0+visionOSwatchOS 9.0+

``` source
nonisolated
func lineLimit(
    _ limit: Int,
    reservesSpace: Bool
) -> some View
```

## Parameters 

`limit`  

The line limit.

`reservesSpace`  

Whether text reserves space so that it always occupies the height required to display the specified number of lines.

## Discussion

Use this modifier to specify a limit to the lines that a `Text` or a vertical `TextField` may occupy. If passed a value of true for the `reservesSpace` parameter, and the text of such views occupies less space than the provided limit, that view expands to occupy the minimum number of lines. When the text occupies more space than the provided limit, a `Text` view truncates its content while a `TextField` becomes scrollable.

```
GroupBox {
    Text("Title")
        .font(.headline)
        .lineLimit(2, reservesSpace: true)
    Text("Subtitle")
        .font(.subheadline)
        .lineLimit(4, reservesSpace: true)
}
```

