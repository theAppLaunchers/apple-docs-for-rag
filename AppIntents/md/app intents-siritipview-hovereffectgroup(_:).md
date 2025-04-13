

- App Intents
- SiriTipView
-  hoverEffectGroup(\_:) 

Instance Method

# hoverEffectGroup(\_:)

Adds a `HoverEffectGroup` to all effects defined on descendant views, and activates the group whenever this view or any descendant views are hovered.

AppIntentsSwiftUIvisionOS 2.0+

``` source
nonisolated
func hoverEffectGroup(_ group: HoverEffectGroup?) -> some View
```

## Parameters 

`group`  

The `HoverEffectGroup` to activate when this view or any subviews are hovered. If `nil`, this modifier has no effect.

## Return Value

A view that activates the given hover group, as well as all effects added to subviews.

## Discussion

You use this modifier when all effects defined on a view and its subviews should activate together. In the following example hovering anywhere over the view will activate the `hoverEffect`s added to the `Text` and the background view, as well as any effects added to the group by other views:

```
struct EffectView: View {
    let effectGroup: HoverEffectGroup?

    var body: some View {
        HStack {
            Image(systemName: "exclamationmark.triangle.fill")
            Text("12 Issues")
                .hoverEffect { effect, isActive, _ in
                    effect.opacity(isActive ? 1 : 0.5)
                }
        }
        .padding()
        .background {
           Capsule()
               .fill(.yellow)
               .hoverEffect { effect, isActive, _ in
                   effect.opacity(isActive ? 0.25 : 0.1)
               }
       }
       .hoverEffectGroup(effectGroup)
   }
}
```

