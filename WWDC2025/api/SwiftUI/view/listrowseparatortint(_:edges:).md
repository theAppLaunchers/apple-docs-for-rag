*   [SwiftUI](/documentation/swiftui)
*   [View](/documentation/swiftui/view)
*   listRowSeparatorTint(\_:edges:)

Instance Method

# listRowSeparatorTint(\_:edges:)

Sets the tint color associated with a row.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 13.0+visionOS 1.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift

```swift
nonisolated
func listRowSeparatorTint(
    _ color: [`Color`](/documentation/swiftui/color)?,
    edges: [`VerticalEdge`](/documentation/swiftui/verticaledge).[`Set`](/documentation/swiftui/verticaledge/set) = .all
) -> some [`View`](/documentation/swiftui/view)
```

```
```
```
```
```
```
```

## [Parameters](/documentation/SwiftUI/View/listRowSeparatorTint\(_:edges:\)#parameters)

`color`

The color to use to tint the row separators, or `nil` to use the default color for the current list style.

`edges`

The set of row edges for which the tint applies. The list style might decide to not display certain separators, typically the top edge. The default is [`all`](/documentation/swiftui/verticaledge/set/all).

## [Discussion](/documentation/SwiftUI/View/listRowSeparatorTint\(_:edges:\)#discussion)

Separators can be presented above and below a row. You can specify to which edge this preference should apply.

This modifier expresses a preference to the containing [`List`](/documentation/swiftui/list). The list style is the final arbiter for the separator tint.

The following example shows a simple grouped list whose row separators are tinted based on row-specific data:

```

```
List {
    ForEach(garage.cars) { car in
        Text(car.model)
            .listRowSeparatorTint(car.brandColor)
    }
}
.listStyle(.grouped)
```

```

To hide a row separators, use [`listRowSeparator(_:edges:)`](/documentation/swiftui/view/listrowseparator\(_:edges:\)). To hide or change the tint color for a section separator, use [`listSectionSeparator(_:edges:)`](/documentation/swiftui/view/listsectionseparator\(_:edges:\)) and [`listSectionSeparatorTint(_:edges:)`](/documentation/swiftui/view/listsectionseparatortint\(_:edges:\)).

## [See Also](/documentation/SwiftUI/View/listRowSeparatorTint\(_:edges:\)#see-also)

### [Configuring separators](/documentation/SwiftUI/View/listRowSeparatorTint\(_:edges:\)#Configuring-separators)

```swift
```swift
```swift
```swift
func listSectionSeparatorTint(Color?, edges: VerticalEdge.Set) -> some View
```
```

Sets the tint color associated with a section.
```
```swift
```swift
```swift
func listRowSeparator(Visibility, edges: VerticalEdge.Set) -> some View
```
```

Sets the display mode for the separator associated with this specific row.
```
```swift
```swift
```swift
func listSectionSeparator(Visibility, edges: VerticalEdge.Set) -> some View
```
```

Sets whether to hide the separator associated with a list section.
```
```