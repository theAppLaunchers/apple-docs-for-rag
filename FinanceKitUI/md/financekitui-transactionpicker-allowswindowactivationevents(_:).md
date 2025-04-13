

- FinanceKitUI
- TransactionPicker
-  allowsWindowActivationEvents(\_:) 

Instance Method

# allowsWindowActivationEvents(\_:)

Configures whether gestures in this view hierarchy can handle events that activate the containing window.

FinanceKitUISwiftUIiOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+visionOS 2.0+

``` source
nonisolated
func allowsWindowActivationEvents(_ value: Bool? = true) -> some View
```

## Parameters 

`value`  

A Boolean value that indicates whether gestures in this view hierarchy can handle events that activate the containing window. If `nil`, or if the modifier is not present, the behavior will be inherited from the view’s ancestors.

## Discussion

Views higher in the hierarchy can override the value you set on this view. In the following example, the tap gesture on the `Rectangle` won’t handle events that activate the containing window because the outer `allowsWindowActivationEvents(_:)` view modifier overrides the inner one:

```
HStack {
    Rectangle()
        .onTapGesture { ... }
        .allowsWindowActivationEvents(true)
}
.allowsWindowActivationEvents(false)
```

Note

It’s only possible to disallow handling events that activate the containing window for views that allow it by default or that inherit this behavior from their ancestors. Views that explicitly already disallow this functionality can’t have it turned on.

