

- Game Controller
- GCControllerLiveInput
-  unmapped 

Instance Property

# unmapped

The live input of a controller without any system-level remapping of the controls.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+

``` source
var unmapped: GCControllerLiveInput? { get }
```

## Discussion

Players should use the system game controller settings to remap controls. If you implement your own controller remapping feature, use this property to access the controller’s physical input without remapping applied.

