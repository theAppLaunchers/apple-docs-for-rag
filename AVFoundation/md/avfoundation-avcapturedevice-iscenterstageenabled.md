

- AVFoundation
- AVCaptureDevice
-  isCenterStageEnabled 

Type Property

# isCenterStageEnabled

A Boolean value that indicates whether a user or an app enabled Center Stage on a device.

iOS 14.5+iPadOS 14.5+Mac Catalyst 14.5+macOS 12.3+tvOS 17.0+

``` source
class var isCenterStageEnabled: Bool { get set }
```

## Discussion

You can only set this value when Center Stage is under app or cooperative control. Attempting to change the enabled state when the control mode is AVCaptureDevice.CenterStageControlMode.user, results in the system throwing an exception.

Note

When Center Stage is under user or cooperative control, the user may change the feature’s enabled state in Control Center. Key-value observe this property value to monitor these changes.

## See Also

### Configuring Center Stage

var isCenterStageActive: Bool

A Boolean value that indicates whether Center Stage is active on a device.

var centerStageRectOfInterest: CGRect

The effective region within the output pixel buffer to perform Center Stage framing.

class var centerStageControlMode: AVCaptureDevice.CenterStageControlMode

A value that indicates the current mode of Center Stage control.

enum CenterStageControlMode

Constants that indicate the current Center Stage control mode.

