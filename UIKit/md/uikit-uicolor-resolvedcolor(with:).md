

- UIKit
- UIColor
-  resolvedColor(with:) 

Instance Method

# resolvedColor(with:)

Returns the version of the current color that results from the specified traits.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+tvOS 13.0+visionOS 1.0+

``` source
func resolvedColor(with traitCollection: UITraitCollection) -> UIColor
```

## Parameters 

`traitCollection`  

The traits to use when resolving the color information.

## Return Value

The version of the color to display for the specified traits.

## Discussion

Use this method when you need to resolve a dynamic color to a specific color value for the specified trait collection. For example, reading the cgColor property or calling getRed(_:green:blue:alpha:) resolves a dynamic color to a specific color value that’s no longer dynamic. If your calling context isn’t inside one of the methods documented in the current property, you need to provide a trait collection from an appropriate trait environment, such as your view or view controller.

The example below uses this method set a border color on a CALayer:

```
// This method sets the border color when UITraitCollection.current is undefined.
func updateBorderColor(layer: CALayer) {

    // Read the trait collection from the view.
    let traitCollection = view.traitCollection
    // Use the trait collection to resolve a dynamic color.
    let borderColor = UIColor.label.resolvedColor(with: traitCollection)
    // Use the CGColor value of the resolved color.
    layer.borderColor = borderColor.cgColor
}
```

## See Also

### Related Documentation

func performAsCurrent(() -> Void)

Executes custom code using the traits of the receiving trait collection.

