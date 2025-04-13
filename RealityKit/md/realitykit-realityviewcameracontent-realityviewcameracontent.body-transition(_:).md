

- RealityKit
- RealityViewCameraContent
- RealityViewCameraContent.Body
-  transition(\_:) 

Instance Method

# transition(\_:)

Associates a transition with the view.

RealityKitSwiftUIiOS 13.0+iPadOS 13.0+Mac CatalystmacOS 10.15+tvOS 13.0+watchOS 6.0+

``` source
nonisolated
func transition(_ t: AnyTransition) -> some View
```

## Discussion

When this view appears or disappears, the transition will be applied to it, allowing for animating it in and out.

The following code will conditionally show MyView, and when it appears or disappears, will use a slide transition to show it.

```
if isActive {
    MyView()
        .transition(.slide)
}
Button("Toggle") {
    withAnimation {
        isActive.toggle()
    }
}
```

