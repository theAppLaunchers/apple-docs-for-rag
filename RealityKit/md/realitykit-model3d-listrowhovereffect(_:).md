

- RealityKit
- Model3D
-  listRowHoverEffect(\_:) 

Instance Method

# listRowHoverEffect(\_:)

Requests that the containing list row use the provided hover effect.

RealityKitSwiftUIvisionOS 1.0+

``` source
nonisolated
func listRowHoverEffect(_ effect: HoverEffect?) -> some View
```

## Parameters 

`effect`  

The hover effect applied to the entire list row.

## Return Value

A view that requests a hover effect for a containing list row

## Discussion

By default, `List` rows have built-in hover effects in visionOS. In some cases, it is useful to change the default hover effect.

This modifier can be applied to a list row’s content to request that the list row’s default effect be replaced by the provided effect. If the view is not contained within a `List` or if the view does not support hover effects in this context, the modifier has no effect.

Use a `nil` effect to indicate that the list row’s default hover effect should not be modified.

`HoverEffect/lift` is not supported for list rows.

