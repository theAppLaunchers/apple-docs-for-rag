

- UIKit
- UIView
-  sizeThatFits(\_:) 

Instance Method

# sizeThatFits(\_:)

Asks the view to calculate and return the size that best fits the specified size.

iOSiPadOSMac CatalysttvOSvisionOS

``` source
@MainActor
func sizeThatFits(_ size: CGSize) -> CGSize
```

## Parameters 

`size`  

The size for which the view should calculate its best-fitting size.

## Return Value

A new size that fits the receiver’s subviews.

## Discussion

The default implementation of this method returns the existing size of the view. Subclasses can override this method to return a custom value based on the desired layout of any subviews. For example, a UISwitch object returns a fixed size value that represents the standard size of a switch view, and a UIImageView object returns the size of the image it is currently displaying.

This method does not resize the receiver.

## See Also

### Related Documentation

var frame: CGRect

The frame rectangle, which describes the view’s location and size in its superview’s coordinate system.

var bounds: CGRect

The bounds rectangle, which describes the view’s location and size in its own coordinate system.

### Configuring the resizing behavior

var contentMode: UIView.ContentMode

A flag used to determine how a view lays out its content when its bounds change.

enum ContentMode

Options to specify how a view adjusts its content when its size changes.

func sizeToFit()

Resizes and moves the receiver view so it just encloses its subviews.

var autoresizesSubviews: Bool

A Boolean value that determines whether the receiver automatically resizes its subviews when its bounds change.

var autoresizingMask: UIView.AutoresizingMask

An integer bit mask that determines how the receiver resizes itself when its superview’s bounds change.

