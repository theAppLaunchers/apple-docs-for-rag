

- RealityKit
- RealityViewCameraContent
- RealityViewCameraContent.Body
-  navigationSplitViewColumnWidth(\_:) 

Instance Method

# navigationSplitViewColumnWidth(\_:)

Sets a fixed, preferred width for the column containing this view.

RealityKitSwiftUIiOS 16.0+iPadOS 16.0+Mac CatalystmacOS 13.0+tvOS 16.0+watchOS 9.0+

``` source
nonisolated
func navigationSplitViewColumnWidth(_ width: CGFloat) -> some View
```

## Discussion

Apply this modifier to the content of a column in a `NavigationSplitView` to specify a fixed preferred width for the column. Use `View/navigationSplitViewColumnWidth(min:ideal:max:)` if you need to specify a flexible width.

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

