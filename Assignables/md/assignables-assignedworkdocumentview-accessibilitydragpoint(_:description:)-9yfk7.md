

- Assignables
- AssignedWorkDocumentView
-  accessibilityDragPoint(\_:description:) 

Instance Method

# accessibilityDragPoint(\_:description:)

The point an assistive technology should use to begin a drag interaction.

AssignablesSwiftUIiOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+visionOS

``` source
nonisolated
func accessibilityDragPoint(
    _ point: UnitPoint,
    description: S
) -> ModifiedContent where S : StringProtocol
```

## Discussion

Use this modifier when you need to provide a description to users when prompted begin a drag interaction.

```
struct FileView: View {
    var filename: String

    var body: some View {
        FileIcon(filename: filename)
            .accessibilityDragPoint(.center, description: "Move \(filename)")
    }
}
```

By default, if an accessible view or its subtree has drag and/or drop interactions, they will be automatically exposed by assistive technologies. However, if there is more than one such interaction, each drag or drop should have a description to disambiguate it and give a good user experience.

Note

An accessibility element can have multiple points for a drag, provided they have different descriptions.

