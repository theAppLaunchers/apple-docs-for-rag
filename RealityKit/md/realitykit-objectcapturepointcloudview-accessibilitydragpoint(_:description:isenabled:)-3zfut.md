

- RealityKit
- ObjectCapturePointCloudView
-  accessibilityDragPoint(\_:description:isEnabled:) 

Instance Method

# accessibilityDragPoint(\_:description:isEnabled:)

The point an assistive technology should use to begin a drag interaction.

RealityKitSwiftUIiOS 18.0+iPadOS 18.0+macOS 15.0+visionOS 2.0+

``` source
nonisolated
func accessibilityDragPoint(
    _ point: UnitPoint,
    description: Text,
    isEnabled: Bool
) -> ModifiedContent
```

## Parameters 

`point`  

The point the assitive technology will begin a drag interaction.

`description`  

The description of the drag interaction.

`isEnabled`  

If true the accessibility drag point is applied; otherwise the accessibility drag point is unchanged.

## Discussion

Use this modifier when you need to provide a description to users when prompted begin a drag interaction.

```
struct FileView: View {
    var filename: String

    var body: some View {
        FileIcon(filename: filename)
            .accessibilityDragPoint(
                .center, description: Text("Move \(filename)"))
    }
}
```

By default, if an accessible view or its subtree has drag and/or drop interactions, they will be automatically exposed by assistive technologies. However, if there is more than one such interaction, each drag or drop should have a description to disambiguate it and give a good user experience.

Note

An accessibility element can have multiple points for a drag, provided they have different descriptions.

