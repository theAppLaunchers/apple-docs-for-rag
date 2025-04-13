

- AVFoundation
- AVCaptureMultiCamSession
-  hardwareCost 

Instance Property

# hardwareCost

A value that indicates the percentage of the session’s available hardware budget currently in use.

iOS 13.0+iPadOS 13.0+Mac Catalyst 14.0+tvOS 17.0+

``` source
var hardwareCost: Float { get }
```

## Discussion

The capture session takes into account the currently connected inputs, outputs, and enabled features to calculate the hardware cost. This value represents the percentage of the hardware in use, normalized to a range of `0.0` to `1.0`. When the value is greater than `1.0`, the capture session cannot run your configuration due to hardware constraints. In this case, you receive an runtimeErrorNotification when you attempt to start the session.

The default value of this property is `0.0`.

## See Also

### Managing Resources

var systemPressureCost: Float

A value that indicates the system pressure cost of the current session configuration.

