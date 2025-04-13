

- FamilyControls
- FamilyActivityPicker
-  scrollTargetBehavior(\_:) 

Instance Method

# scrollTargetBehavior(\_:)

Sets the scroll behavior of views scrollable in the provided axes.

FamilyControlsSwiftUIiOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+watchOS 10.0+

``` source
nonisolated
func scrollTargetBehavior(_ behavior: some ScrollTargetBehavior) -> some View
```

## Discussion

A scrollable view calculates where scroll gestures should end using its deceleration rate and the state of its scroll gesture by default. A scroll behavior allows for customizing this logic. You can provide your own `ScrollTargetBehavior` or use one of the built in behaviors provided by SwiftUI.

### Paging Behavior

SwiftUI offers a `PagingScrollTargetBehavior` behavior which uses the geometry of the scroll view to decide where to allow scrolls to end.

In the following example, every view in the lazy stack is flexible in both directions and the scroll view will settle to container aligned boundaries.

```
ScrollView {
    LazyVStack(spacing: 0.0) {
        ForEach(items) { item in
            FullScreenItem(item)
        }
    }
}
.scrollTargetBehavior(.paging)
```

### View Aligned Behavior

SwiftUI offers a `ViewAlignedScrollTargetBehavior` scroll behavior that will always settle on the geometry of individual views.

```
ScrollView(.horizontal) {
    LazyHStack(spacing: 10.0) {
        ForEach(items) { item in
            ItemView(item)
        }
    }
    .scrollTargetLayout()
}
.scrollTargetBehavior(.viewAligned)
.safeAreaPadding(.horizontal, 20.0)
```

You configure which views should be used for settling using the `View/scrollTargetLayout(isEnabled:)` modifier. Apply this modifier to a layout container like `LazyVStack` or `HStack` and each individual view in that layout will be considered for alignment.

