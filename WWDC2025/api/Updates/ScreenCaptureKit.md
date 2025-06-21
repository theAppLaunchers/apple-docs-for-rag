*   [Updates](/documentation/updates)
*   ScreenCaptureKit updates

Article

# ScreenCaptureKit updates

Learn about important changes to ScreenCaptureKit.

## [Overview](/documentation/Updates/ScreenCaptureKit#Overview)

Browse notable changes in [ScreenCaptureKit](/documentation/ScreenCaptureKit).

## [June 2024](/documentation/Updates/ScreenCaptureKit#June-2024)

### [AppKit](/documentation/Updates/ScreenCaptureKit#AppKit)

*   Share an app window with a remote viewer on demand with `requestSharingOfWindow(_ window: NSWindow, completionHandler: @escaping ((any Error)?)`. This method enables an app to share a window in response to a specific action, such as when a person clicks play in a document window, and streamlines a previously multistep window-sharing process.
    
*   Share a preview of a window with a remote viewer on demand with `requestSharingOfWindow(usingPreview image: NSImage, title: String, completionHandler: @escaping ((any Error)?)`, which causes the framework to call a delegate method to provide the window if there’s a valid sharing session and a person confirms the offer to share.
    

### [SwiftUI](/documentation/Updates/ScreenCaptureKit#SwiftUI)

*   Create new, sharable windows using the async function `openWindow(id: String, sharingBehavior: SharingBehavior)`. This method gives presenting apps a way to share just the window they want recipients to see, even if that window takes over the entire screen and doesn’t allow access to the window picker, streamlining a previously multistep window-sharing process.
    

### [ScreenCaptureKit](/documentation/Updates/ScreenCaptureKit#ScreenCaptureKit)

*   Capture screenshots across multiple displays.
    
*   Capture HDR content by adopting the `captureDynamicRange` property in `SCStreamConfiguration`, which allows clients to choose between `SCCaptureModeSDR`, `SCCaptureModeHDRLocalDisplay`, and `SCCaptureModeHDRCanonicalDisplay` modes. Or use `SCStreamConfigurationPreset` to simplify the selection of properties needed for capture HDR.
    
*   Capture microphone audio by streaming output with the `SCStreamOutputTypeMicrophone` type to a sample handler queue that the framework processes and returns audio samples in buffers to the client via the stream’s `didOutputSampleBuffer` delegate method.
    
*   Record a stream’s screen, audio, and microphone output to a file using the `outputURL` property of `SCRecordingOutput`, which enables you to specify where the framework saves a recording file. Properties available in `SCRecordingOutputConfiguration` allow you to select the characteristics of the recording by choosing the file and codec types for the recording. The `SCRecordingOutputConfiguration` class methods enable you to enumerate the available codecs and file types ScreenCaptureKit supports.
    
*   Start and stop recordings with two new methods on `SCStream` using `addRecordingOutput` and `removeRecordingOutput`.
    
*   Respond to events occur during the process of recording to a file with `SCRecordingOutputDelegate`.
    

## [June 2023](/documentation/Updates/ScreenCaptureKit#June-2023)

*   Use the new sharing picker: [`SCContentSharingPicker`](/documentation/ScreenCaptureKit/SCContentSharingPicker).
    
*   Access new properties of [`AVCaptureDevice`](/documentation/AVFoundation/AVCaptureDevice) for status on effects relevant to screen capture.
    
*   Take screenshots with [`SCStream`](/documentation/ScreenCaptureKit/SCStream).
    
*   Deprecated `CGStream`. Use [`SCStreamConfiguration`](/documentation/ScreenCaptureKit/SCStreamConfiguration) instead.
    

## [See Also](/documentation/Updates/ScreenCaptureKit#see-also)

### [Technology updates](/documentation/Updates/ScreenCaptureKit#Technology-updates)

[

Accelerate updates](/documentation/updates/accelerate)

Learn about important changes to Accelerate.

[

Accessibility updates](/documentation/updates/accessibility)

Learn about important changes to Accessibility.

[

ActivityKit updates](/documentation/updates/activitykit)

Learn about important changes in ActivityKit.

[

AdAttributionKit Updates](/documentation/updates/adattributionkit)

Learn about important changes to AdAttributionKit.

[

App Clips updates](/documentation/updates/appclips)

Learn about important changes in App Clips.

[

App Intents updates](/documentation/updates/appintents)

Learn about important changes in App Intents.

[

AppKit updates](/documentation/updates/appkit)

Learn about important changes to AppKit.

[

Apple Intelligence updates](/documentation/updates/apple-intelligence)

Learn about important changes to Apple Intelligence.

[

AppleMapsServerAPI Updates](/documentation/updates/applemapsserverapi)

Learn about important changes to AppleMapsServerAPI.

[

Apple Pencil updates](/documentation/updates/applepencil)

Learn about important changes to Apple Pencil.

[

ARKit updates](/documentation/updates/arkit)

Learn about important changes to ARKit.

[

Audio Toolbox updates](/documentation/updates/audiotoolbox)

Learn about important changes to Audio Toolbox.

[

AuthenticationServices updates](/documentation/updates/authenticationservices)

Learn about important changes to AuthenticationServices.

[

AVFAudio updates](/documentation/updates/avfaudio)

Learn about important changes to AVFAudio.

[

AVFoundation updates](/documentation/updates/avfoundation)

Learn about important changes to AVFoundation.