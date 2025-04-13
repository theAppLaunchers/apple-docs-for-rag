

- FamilyControls
- FamilyActivityPicker
-  listSectionSeparator(\_:edges:) 

Instance Method

# listSectionSeparator(\_:edges:)

Sets whether to hide the separator associated with a list section.

FamilyControlsSwiftUIiOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 13.0+

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

## See Also

### Visibility

func hidden() -> some View

Hides this view unconditionally.

func labelsHidden() -> some View

Hides the labels of any controls contained within this view.

func menuIndicator(Visibility) -> some View

Sets the menu indicator visibility for controls within this view.

func listRowSeparator(Visibility, edges: VerticalEdge.Set) -> some View

Sets the display mode for the separator associated with this specific row.

