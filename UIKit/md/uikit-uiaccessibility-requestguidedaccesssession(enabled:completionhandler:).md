

- UIKit
- UIAccessibility
-  requestGuidedAccessSession(enabled:completionHandler:) 

Type Method

# requestGuidedAccessSession(enabled:completionHandler:)

Transitions the app to or from Single App mode asynchronously.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+tvOSvisionOS 1.0+

``` source
@MainActor
static func requestGuidedAccessSession(
    enabled enable: Bool,
    completionHandler: @escaping @MainActor (Bool) -> Void
)
```

## Parameters 

`enable`  

Specify true to put the device into Single App mode for this app or false to exit Single App mode.

`completionHandler`  

The block that notifies your app of the success or failure of the operation. This block takes the following parameter:

didSucceed  
If true, the app transitioned to or from Single App mode successfully. If false, the app or device is not eligible for Single App mode or there was some other error.

## Discussion

You can use this method to lock your app into Single App mode and to release it from that mode later. For example, a test-taking app might enter this mode at the beginning of a test and exit it when the user completes the test. Entering Single App mode is supported only for devices that are supervised using Mobile Device Management (MDM), and the app itself must be enabled for this mode by MDM. You must balance each call to enter Single App mode with a call to exit that mode.

Because entering or exiting Single App mode might take some time, this method executes asynchronously and notifies you of the results using the `completionHandler` block.

## See Also

### Convenience functions

static func focusedElement(using: UIAccessibility.AssistiveTechnologyIdentifier?) -> Any?

Returns the accessibility element that’s currently in focus by the specified assistive app.

static var hearingDevicePairedEar: UIAccessibility.HearingDeviceEar

The current pairing status of Made for iPhone hearing devices.

struct HearingDeviceEar

Constants that specify how a person is using a hearing device.

static func registerGestureConflictWithZoom()

Warns users that app-specific gestures conflict with the system-defined Zoom accessibility gestures.

static func zoomFocusChanged(zoomType: UIAccessibility.ZoomType, toFrame: CGRect, in: UIView)

Notifies the system when the app’s focus changes to a new location.

