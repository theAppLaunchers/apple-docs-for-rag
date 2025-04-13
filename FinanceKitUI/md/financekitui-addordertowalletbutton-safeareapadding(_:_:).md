

- FinanceKitUI
- AddOrderToWalletButton
-  safeAreaPadding(\_:\_:) 

Instance Method

# safeAreaPadding(\_:\_:)

Adds the provided insets into the safe area of this view.

FinanceKitUISwiftUIiOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+watchOS 10.0+

``` source
nonisolated
func safeAreaPadding(
    _ edges: Edge.Set = .all,
    _ length: CGFloat? = nil
) -> some View
```

## Discussion

Use this modifier when you would like to add a fixed amount of space to the safe area a view sees.

```
ScrollView(.horizontal) {
    HStack(spacing: 10.0) {
        ForEach(items) { item in
            ItemView(item)
        }
    }
}
.safeAreaPadding(.horizontal, 20.0)
```

See the `View/safeAreaInset(edge:alignment:spacing:content)` modifier for adding to the safe area based on the size of a view.

