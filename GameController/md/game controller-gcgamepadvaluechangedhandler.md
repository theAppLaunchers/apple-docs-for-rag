

- Game Controller
-  GCGamepadValueChangedHandler 

Type Alias

# GCGamepadValueChangedHandler

Signature for the block executed if any element in the gamepad profile changes value.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+macOS 10.9+tvOS 9.0+visionOS 1.0+

``` source
typealias GCGamepadValueChangedHandler = (GCGamepad, GCControllerElement) -> Void
```

## Discussion

The block parameters are defined as follows:

`gamepad`  
The profile object whose value changed.

`element`  
The element whose value changed.

If multiple elements change values at the same time, the block is called once for each element that changed. The block is called only for the elements directly attached to the profile object; if a child element of one of those elements changes values, the block is called for the parent.

This block type is used by the valueChangedHandler property.

