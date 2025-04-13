

- Game Controller
-  GCMouseMoved 

Type Alias

# GCMouseMoved

The signature for the block that the mouse input profile calls when the mouse moves.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 14.0+visionOS 1.0+

``` source
typealias GCMouseMoved = (GCMouseInput, Float, Float) -> Void
```

## Parameters 

`mouse`  

The controller for the physical mouse.

`deltaX`  

The raw amount that the mouse moves along the x-axis without affecting mouse sensitivity settings.

`deltaY`  

The raw amount that the mouse moves along the y-axis without affecting mouse sensitivity settings.

## See Also

### Getting Change Information

var mouseMovedHandler: GCMouseMoved?

The block that the profile calls when the mouse moves.

