

- RealityKit
- Model3D
-  accessibilityHint(\_:) 

Instance Method

# accessibilityHint(\_:)

Communicates to the user what happens after performing the view’s action.

RealityKitSwiftUIiOS 14.0+iPadOS 14.0+macOS 11.0+tvOS 14.0+visionOSwatchOS 7.0+

``` source
nonisolated
func accessibilityHint(_ hint: Text) -> ModifiedContent
```

## Discussion

Provide a hint in the form of a brief phrase, like “Purchases the item” or “Downloads the attachment”.

Note

On macOS, if the view does not have an action and it has been made into a container with `accessibilityElement(children: .contain)`, this will be used to describe the container. For example, if the container is for a graph, the hint could be “graph”.

