

- AVFoundation
- AVCaptureDevice
-  companionDeskViewCamera 

Instance Property

# companionDeskViewCamera

A Desk View camera associated with a device.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 17.0+

``` source
var companionDeskViewCamera: AVCaptureDevice? { get }
```

## Discussion

The value provides an Desk View camera for a device, if one exists, that derives its framing from the device’s ultra wide camera. When multiple Continuity Camera devices are available on the system, use this property to a relate a particular instance with its associated Desk View device.

## See Also

### Supporting Continuity Camera

class var systemPreferredCamera: AVCaptureDevice?

A camera the system prefers to use for video and photo capture.

class var userPreferredCamera: AVCaptureDevice?

A camera the user prefers to use for video and photo capture.

var isContinuityCamera: Bool

A Boolean value that indicates whether the device is a Continuity Camera.

