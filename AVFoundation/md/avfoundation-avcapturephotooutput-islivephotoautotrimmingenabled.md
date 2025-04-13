

- AVFoundation
- AVCapturePhotoOutput
-  isLivePhotoAutoTrimmingEnabled 

Instance Property

# isLivePhotoAutoTrimmingEnabled

A Boolean value that indicates whether to automatically trim Live Photo movie captures to avoid excessive movement.

iOS 10.0+iPadOS 10.0+Mac Catalyst 14.0+tvOS 17.0+

``` source
var isLivePhotoAutoTrimmingEnabled: Bool { get set }
```

## Discussion

This value defaults to true when isLivePhotoCaptureSupported is true.

Use this option to enable the same automatic trimming behavior found in the Camera app. By default, a Live Photo capture is about three seconds in duration, centered on the time of the capture request. If the user moves the camera during capture, iOS analyzes the capture and automatically trims the duration of the Live Photo to avoid capturing excess movement.

Changing this value while your session is running requires a lengthy reconfiguration of the session. If you intend to take any Live Photo captures, set this value to true before calling AVCaptureSession startRunning(). If you change this property while the session is running, in-progress Live Photo captures end immediately, unfulfilled photo requests cancel, and the video preview temporarily freezes.

## See Also

### Configuring Live Photo Capture

var isLivePhotoCaptureSupported: Bool

A Boolean value that indicates whether the capture output currently supports Live Photo capture.

var isLivePhotoCaptureEnabled: Bool

A Boolean value that indicates whether to configure the capture pipeline for Live Photo capture.

var isLivePhotoCaptureSuspended: Bool

A Boolean value that indicates whether Live Photo capture is currently in a suspended state.

var preservesLivePhotoCaptureSuspendedOnSessionStop: Bool

A Boolean value that indicates whether to preserve the suspended state of Live Photo capture when the session stops.

var availableLivePhotoVideoCodecTypes: [AVVideoCodecType]

An array of video codecs currently available for Live Photo movie captures.

