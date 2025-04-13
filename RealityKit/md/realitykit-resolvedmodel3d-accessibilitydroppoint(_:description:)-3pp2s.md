

- RealityKit
- ResolvedModel3D
-  accessibilityDropPoint(\_:description:) 

Instance Method

# accessibilityDropPoint(\_:description:)

The point an assistive technology should use to end a drag interaction.

RealityKitSwiftUIiOS 16.0+iPadOS 16.0+macOS 13.0+visionOS

``` source
nonisolated
func accessibilityDropPoint(
    _ point: UnitPoint,
    description: Text
) -> ModifiedContent
```

## Discussion

Use this modifier when you need to provide a description to users when prompted end a drag interaction.

```
struct FolderView: View {
    var folderName: String

    var body: some View {
        FolderIcon(folderName: folderName)
            .accessibilityDropPoint(.center, description: Text("Move to \(folderName)"))
    }
}
```

By default, if an accessible view or its subtree has drag and/or drop interactions, they will be automatically exposed by assistive technologies. However, if there is more than one such interaction, each drag or drop should have a description to disambiguate it and give a good user experience.

Note

An accessibility element can have multiple points for a drop, provided they have different descriptions.

