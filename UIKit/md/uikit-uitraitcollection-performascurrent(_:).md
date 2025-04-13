

- UIKit
- UITraitCollection
-  performAsCurrent(\_:) 

Instance Method

# performAsCurrent(\_:)

Executes custom code using the traits of the receiving trait collection.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+tvOS 13.0+visionOS 1.0+

``` source
func performAsCurrent(_ actions: () -> Void)
```

## Parameters 

`actions`  

A closure containing the code you want to execute. This closure has no return value and takes no parameters.

## Discussion

The current property is undefined outside the documented methods where UIKit sets it. Use this method when you want to execute code that relies on the current property from outside these methods. You can also use this method if you want to execute some code using the traits of a different trait environment. Prefer this method over manually setting the current property yourself.

This method temporarily replaces the traits of the current environment with the ones in the targeted UITraitCollection. After the `actions` block finishes, the method restores the original traits to the environment. You can call this method from any thread of your app.

The example below shows how you can safely resolve dynamic UIColor that relies on current:

```
func updateBorderColor(layer: CALayer) {

    // Read the trait collection from the view.
    let traitCollection = view.traitCollection
    traitCollection.performAsCurrent {
        // Inside the closure, the current property is set to traitCollection,
        // which UIColor uses to resolve the dynamic color borderColor.
        layer.borderColor = UIColor.label.cgColor
    }
}
```

