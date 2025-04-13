

- MusicKit
- ArtworkImage
-  listSectionSeparator(\_:edges:) 

Instance Method

# listSectionSeparator(\_:edges:)

Sets whether to hide the separator associated with a list section.

MusicKitSwiftUIiOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 13.0+visionOS 1.0+

``` source
nonisolated
func listSectionSeparator(
    _ visibility: Visibility,
    edges: VerticalEdge.Set = .all
) -> some View
```

## Parameters 

`visibility`  

The visibility of this section’s separators.

`edges`  

The set of row edges for which the preference applies. The list style might already decide to not display separators for some edges. The default is `VerticalEdge/Set/all`.

## Discussion

Separators can be presented above and below a section. You can specify to which edge this preference should apply.

This modifier expresses a preference to the containing `List`. The list style is the final arbiter of the separator visibility.

The following example shows a simple grouped list whose bottom sections separator are hidden:

```
List {
    ForEach(garage) { garage in
        Section(header: Text(garage.location)) {
            ForEach(garage.cars) { car in
                Text(car.model)
                    .listRowSeparatorTint(car.brandColor)
            }
        }
        .listSectionSeparator(.hidden, edges: .bottom)
    }
}
.listStyle(.grouped)
```

To change the visibility and tint color for a row separator, use `View/listRowSeparator(_:edges:)` and `View/listRowSeparatorTint(_:edges:)`. To set the tint color for a section separator, use `View/listSectionSeparatorTint(_:edges:)`.

