

- Assignables
- AssignableDocumentView
-  navigationSplitViewColumnWidth(min:ideal:max:) 

Instance Method

# navigationSplitViewColumnWidth(min:ideal:max:)

Sets a flexible, preferred width for the column containing this view.

AssignablesSwiftUIiOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOSwatchOS 9.0+

``` source
nonisolated
func navigationSplitViewColumnWidth(
    min: CGFloat? = nil,
    ideal: CGFloat,
    max: CGFloat? = nil
) -> some View
```

## Discussion

Apply this modifier to the content of a column in a `NavigationSplitView` to specify a preferred flexible width for the column. Use `View/navigationSplitViewColumnWidth(_:)` if you need to specify a fixed width.

The following example shows a three-column navigation split view where the first column has a preferred width of 150 points, and the second column has a flexible, preferred width between 150 and 400 points:

```
NavigationSplitView {
    MySidebar()
        .navigationSplitViewColumnWidth(150)
} contents: {
    MyContents()
        .navigationSplitViewColumnWidth(
            min: 150, ideal: 200, max: 400)
} detail: {
    MyDetail()
}
```

Only some platforms enable resizing columns. If you specify a width that the current presentation environment doesn’t support, SwiftUI may use a different width for your column.

