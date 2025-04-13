

- SwiftUI
- View
-  listRowHoverEffectDisabled(\_:) 

Instance Method

# listRowHoverEffectDisabled(\_:)

Requests that the containing list row have its hover effect disabled.

visionOS 1.0+

``` source
nonisolated
func listRowHoverEffectDisabled(_ disabled: Bool = true) -> some View
```

## Parameters 

`disabled`  

A Boolean value that determines whether the containing list row should display its default hover effect.

## Return Value

A view that requests the default hover effect on its containing list row to conditionally be disabled.

## Discussion

By default, `List` rows have built-in hover effects in visionOS. In some cases, it is useful to disable the default hover effect.

## See Also

### Configuring rows

func listRowInsets(EdgeInsets?) -> some View

Applies an inset to the rows in a list.

func listRowHoverEffect(HoverEffect?) -> some View

Requests that the containing list row use the provided hover effect.

func listItemTint(_:)

Sets a fixed tint color for content in a list.

struct ListItemTint

A tint effect configuration that you can apply to content in a list.

var defaultMinListRowHeight: CGFloat

The default minimum height of a row in a `List`. The default minimum height of a row in a list.

