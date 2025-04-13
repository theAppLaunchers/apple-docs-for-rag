

- Assignables
- AssignedWorkDocumentView
-  frame(depth:alignment:) 

Instance Method

# frame(depth:alignment:)

Positions this view within an invisible frame with the specified depth.

AssignablesSwiftUIvisionOS 1.0+

``` source
nonisolated
func frame(
    depth: CGFloat?,
    alignment: DepthAlignment = .center
) -> some View
```

## Parameters 

`depth`  

A fixed depth for the resulting view. If `depth` is `nil`, the resulting view assumes this view’s sizing behavior.

`alignment`  

The alignment of this view inside the resulting view. `alignment` applies if this view is smaller than the size given by the resulting frame.

## Return Value

A view with a fixed dimension of `depth` if non-`nil`.

## Discussion

Use this method to specify a fixed size for a view’s depth. If you don’t specify a dimension, the resulting view assumes this view’s sizing behavior in depth.

