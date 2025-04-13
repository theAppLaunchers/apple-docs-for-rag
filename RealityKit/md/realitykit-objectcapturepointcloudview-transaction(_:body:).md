

- RealityKit
- ObjectCapturePointCloudView
-  transaction(\_:body:) 

Instance Method

# transaction(\_:body:)

Applies the given transaction mutation function to all animations used within the `body` closure.

RealityKitSwiftUIiOS 17.0+iPadOS 17.0+macOS 14.0+tvOS 17.0+watchOS 10.0+

``` source
nonisolated
func transaction(
    _ transform: @escaping (inout Transaction) -> Void,
    @ViewBuilder body: (PlaceholderContentView) -> V
) -> some View where V : View
```

## Discussion

Any modifiers applied to the content of `body` will be applied to this view, and the changes to the transaction performed in the `transform` will only affect the modifiers defined in the `body`.

The following code animates the opacity changing with a faster animation, while the contents of MyView are animated with the implicit transaction:

```
MyView(isActive: isActive)
    .transaction { transaction in
        transaction.animation = transaction.animation?.speed(2)
    } body: { content in
        content.opacity(isActive ? 1.0 : 0.0)
    }
```

- See Also: `Transaction.disablesAnimations`

