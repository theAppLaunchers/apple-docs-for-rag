

- Assignables
- AssignableDocumentView
-  onImmersionChange(initial:\_:) 

Instance Method

# onImmersionChange(initial:\_:)

Performs an action when the immersion state of your app changes.

AssignablesSwiftUIvisionOS 2.0+

``` source
nonisolated
func onImmersionChange(
    initial: Bool = true,
    _ action: @escaping (ImmersionChangeContext, ImmersionChangeContext) -> Void
) -> some View
```

## Parameters 

`initial`  

Whether the action should be run when this view initially appears.

`action`  

A closure to run when the immersion changes.

`oldValue`  

The value representing the old state of immersion.

`newValue`  

The value representing the current state of immersion.

## Discussion

Depending on the immersion style used for the Immersive Space in your app, the amount of immersion can be controlled by actions such as turning the Digital Crown. Use this modifier to define a closure that is run when the immersion state changes. The following example sets the value of a binding depending on the current amount of immersion:

```
struct ImmersiveView: View {
    @Binding var enableSoundEffects: Bool

    var body: some View {
        MyView()
            .onImmersionChange { _, newImmersion in
                guard let amount = newImmersion.amount else {
                    enableSoundEffects = false
                    return
                }
                // Enable some effects based on the updated
                // amount of immersion
                enableSoundEffects = amount > 0.5
            }
    }
}
```

