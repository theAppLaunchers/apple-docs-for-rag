*   [AVFoundation](/documentation/avfoundation)
*   AVCaptureDevice

Class

# AVCaptureDevice

An object that represents a hardware or virtual capture device like a camera or microphone.

iOS 4.0+iPadOS 4.0+Mac Catalyst 14.0+macOS 10.7+tvOS 17.0+visionOS 1.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
class AVCaptureDevice
```
```
```
```
```
```
```
```

## [Mentioned in](/documentation/AVFoundation/AVCaptureDevice#mentions)

[

Requesting authorization to capture and save media](/documentation/avfoundation/requesting-authorization-to-capture-and-save-media)

[

Setting Up a Capture Session](/documentation/avfoundation/setting-up-a-capture-session)

[

Choosing a Capture Device](/documentation/avfoundation/choosing-a-capture-device)

[

Enhancing your app experience with the Camera Control](/documentation/avfoundation/enhancing-your-app-experience-with-the-camera-control)

## [Overview](/documentation/AVFoundation/AVCaptureDevice#overview)

Capture devices provide media data to capture session inputs that you connect to an [`AVCaptureSession`](/documentation/avfoundation/avcapturesession). An individual device can provide one or more streams of media of a particular type.

You don’t create capture device instances directly. Instead, retrieve them using an instance of [`AVCaptureDevice.DiscoverySession`](/documentation/avfoundation/avcapturedevice/discoverysession), or by calling the [`default(_:for:position:)`](/documentation/avfoundation/avcapturedevice/default\(_:for:position:\)) method.

A capture device provides several configuration options. Before attempting to configure device properties, such as its focus mode, exposure mode, and so on, you must first acquire a lock on the device by calling the [`lockForConfiguration()`](/documentation/avfoundation/avcapturedevice/lockforconfiguration\(\)) method. You should also query the device’s capabilities to ensure that the new modes you intend to set are valid for the device. You can then set the properties and release the lock using the [`unlockForConfiguration()`](/documentation/avfoundation/avcapturedevice/unlockforconfiguration\(\)) method. You may hold the lock if you want all settable device properties to remain unchanged. However, holding the device lock unnecessarily may degrade capture quality in other apps sharing the device and isn’t recommended.

## [Topics](/documentation/AVFoundation/AVCaptureDevice#topics)

### [Finding and Monitoring Devices](/documentation/AVFoundation/AVCaptureDevice#Finding-and-Monitoring-Devices)

```swift
```swift
```swift
```swift
class DiscoverySession
```
```

An object that finds capture devices that match specific search criteria.
```
```swift
```swift
```swift
class func `default`(AVCaptureDevice.DeviceType, for: AVMediaType?, position: AVCaptureDevice.Position) -> AVCaptureDevice?
```
```

Returns the default device for the specified device type, media type, and position.
```
```swift
```swift
```swift
class func `default`(for: AVMediaType) -> AVCaptureDevice?
```
```

Returns the default device that captures the specified media type.
```

[`init?(uniqueID: String)`](/documentation/avfoundation/avcapturedevice/init\(uniqueid:\))

Creates an object that represents a device with the specified identifier.

```swift
```swift
```swift
class let wasConnectedNotification: NSNotification.Name
```
```

A notification the system posts when a new capture device becomes available.
```
```swift
```swift
```swift
class let wasDisconnectedNotification: NSNotification.Name
```
```

A notification the system posts when an existing device becomes unavailable.
```
```swift
```swift
```swift
class func devices(for: AVMediaType) -> [AVCaptureDevice]
```
```

Returns devices capable of capturing media of the specified type.

Deprecated
```
```swift
```swift
```swift
class func devices() -> [AVCaptureDevice]
```
```

Returns all available capture devices on the system.

Deprecated
```
```

### [Authorizing Device Access](/documentation/AVFoundation/AVCaptureDevice#Authorizing-Device-Access)

```swift
```swift
```swift
```swift
class func requestAccess(for: AVMediaType, completionHandler: (Bool) -> Void)
```
```

Requests the user’s permission to allow the app to capture media of a particular type.
```
```swift
```swift
```swift
class func authorizationStatus(for: AVMediaType) -> AVAuthorizationStatus
```
```

Returns an authorization status that indicates whether the user grants the app permission to capture media of a particular type.
```
```swift
```swift
```swift
enum AVAuthorizationStatus
```
```

Constants that indicate the status of an app’s authorization to capture media.
```
```

### [Identifying a Device](/documentation/AVFoundation/AVCaptureDevice#Identifying-a-Device)

```swift
```swift
```swift
```swift
var uniqueID: String
```
```

An identifier that uniquely identifies the device.
```
```swift
```swift
```swift
var modelID: String
```
```

A model identifier for the device.
```
```swift
```swift
```swift
var localizedName: String
```
```

A localized device name for display in the user interface.
```
```swift
```swift
```swift
var manufacturer: String
```
```

A human-readable string for the manufacturer of the device.
```
```swift
```swift
```swift
var deviceType: AVCaptureDevice.DeviceType
```
```

The type of device, such as a built-in microphone or wide-angle camera.
```
```swift
```swift
```swift
struct DeviceType
```
```

A structure that defines the device types the framework supports.
```
```swift
```swift
```swift
var position: AVCaptureDevice.Position
```
```

The physical position of the capture device hardware.
```
```swift
```swift
```swift
enum Position
```
```

Constants that indicate the physical position of a capture device.
```
```

### [Accessing Device State](/documentation/AVFoundation/AVCaptureDevice#Accessing-Device-State)

```swift
```swift
```swift
```swift
var isConnected: Bool
```
```

A Boolean value that indicates whether a device is currently connected to the system and available for use.
```
```swift
```swift
```swift
var isSuspended: Bool
```
```

A Boolean value that indicates whether the device is in a suspended state.
```
```swift
```swift
```swift
var isInUseByAnotherApplication: Bool
```
```

A Boolean value that indicates whether another app is using the device.
```
```

### [Inspecting Device Characteristics](/documentation/AVFoundation/AVCaptureDevice#Inspecting-Device-Characteristics)

```swift
```swift
```swift
```swift
var isVirtualDevice: Bool
```
```

A Boolean value that indicates whether the device consists of two or more physical devices.
```
```swift
```swift
```swift
var constituentDevices: [AVCaptureDevice]
```
```

An array of physical devices that make up a virtual device.
```
```swift
```swift
```swift
func hasMediaType(AVMediaType) -> Bool
```
```

Returns a Boolean value that indicates whether the device captures media of a particular type.
```
```swift
```swift
```swift
var transportType: Int32
```
```

The transport type of the device.
```
```swift
```swift
```swift
func supportsSessionPreset(AVCaptureSession.Preset) -> Bool
```
```

Returns a Boolean value that indicates whether you can use the device with capture session configured with the specified preset.
```
```

### [Monitoring Device Rotation](/documentation/AVFoundation/AVCaptureDevice#Monitoring-Device-Rotation)

```swift
```swift
```swift
```swift
class RotationCoordinator
```
```

A class that monitors the physical orientation of a capture device and provides adjustment angles to keep images level, relative to gravity.
```
```

### [Configuring Camera Hardware](/documentation/AVFoundation/AVCaptureDevice#Configuring-Camera-Hardware)

```swift
```swift
```swift
```swift
func lockForConfiguration() throws
```
```

Requests exclusive access to configure device hardware properties.
```
```swift
```swift
```swift
func unlockForConfiguration()
```
```

Releases exclusive control over device hardware properties.
```
```swift
```swift
```swift
var isSubjectAreaChangeMonitoringEnabled: Bool
```
```

A Boolean value that indicates whether the device monitors the subject area for changes.
```
```swift
```swift
```swift
class let subjectAreaDidChangeNotification: NSNotification.Name
```
```

A notification the system posts when a capture device detects a substantial change to the video subject area.
```

[

API Reference

Formats](/documentation/avfoundation/capture-device-formats)

Configure capture formats and camera frame rates.

[

API Reference

Focus](/documentation/avfoundation/capture-device-focus)

Configure the automatic focus behavior of a camera, or manually set its lens position.

[

API Reference

Exposure](/documentation/avfoundation/capture-device-exposure)

Configure the automatic exposure behavior of a camera, or manually control its exposure settings.

[

API Reference

White Balance](/documentation/avfoundation/capture-device-white-balance)

Configure the automatic white balance behavior of a camera, or manually control white balance settings.

[

API Reference

Lighting](/documentation/avfoundation/capture-device-lighting)

Configure the device flash, torch, and low light settings.

[

API Reference

Color](/documentation/avfoundation/capture-device-color)

Manage HDR and color space settings for a device.

[

API Reference

Zoom](/documentation/avfoundation/capture-device-zoom)

Configure device zooming behavior and inspect hardware capabilities.
```

### [Enabling Automatic Frame Rate](/documentation/AVFoundation/AVCaptureDevice#Enabling-Automatic-Frame-Rate)

```swift
```swift
```swift
```swift
var isAutoVideoFrameRateEnabled: Bool
```
```

A Boolean value that indicates whether the capture device performs automatic video frame rate adjustments.
```
```

### [Supporting Spatial Capture](/documentation/AVFoundation/AVCaptureDevice#Supporting-Spatial-Capture)

```swift
```swift
```swift
```swift
var spatialCaptureDiscomfortReasons: Set<AVSpatialCaptureDiscomfortReason>
```
```

Reasons why current environmental conditions aren’t suitable to capturing spatial videos that are comfortable to view.
```
```swift
```swift
```swift
struct AVSpatialCaptureDiscomfortReason
```
```

Constants that indicate the suitability of the current scene to create a comfortable viewing experience.
```
```

### [Supporting Continuity Camera](/documentation/AVFoundation/AVCaptureDevice#Supporting-Continuity-Camera)

```swift
```swift
```swift
```swift
class var systemPreferredCamera: AVCaptureDevice?
```
```

A camera the system prefers to use for video and photo capture.
```
```swift
```swift
```swift
class var userPreferredCamera: AVCaptureDevice?
```
```

A camera the user prefers to use for video and photo capture.
```
```swift
```swift
```swift
var isContinuityCamera: Bool
```
```

A Boolean value that indicates whether the device is a Continuity Camera.
```
```swift
```swift
```swift
var companionDeskViewCamera: AVCaptureDevice?
```
```

A Desk View camera associated with a device.
```
```

### [Supporting System Features](/documentation/AVFoundation/AVCaptureDevice#Supporting-System-Features)

[

API Reference

System Video Effects and Microphone Modes](/documentation/avfoundation/system-video-effects-and-microphone-modes)

Configure the state of system video effects like Center Stage, and inspect enhancements the system applies to microphone audio.

### [Monitoring System Pressure](/documentation/AVFoundation/AVCaptureDevice#Monitoring-System-Pressure)

```swift
```swift
```swift
```swift
var systemPressureState: AVCaptureDevice.SystemPressureState
```
```

A value that indicates the capture device’s current system pressure state.
```
```swift
```swift
```swift
class SystemPressureState
```
```

An object that provides information about OS and hardware status affecting capture system performance and availability.
```
```swift
```swift
```swift
let AVCaptureSessionInterruptionSystemPressureStateKey: String
```
```

A key to retrieve a state value that indicates the system pressure level and contributing factors that caused the interruption.
```
```

### [Restricting Camera Switching](/documentation/AVFoundation/AVCaptureDevice#Restricting-Camera-Switching)

```swift
```swift
```swift
```swift
func setPrimaryConstituentDeviceSwitchingBehavior(AVCaptureDevice.PrimaryConstituentDeviceSwitchingBehavior, restrictedSwitchingBehaviorConditions: AVCaptureDevice.PrimaryConstituentDeviceRestrictedSwitchingBehaviorConditions)
```
```

Sets the switching behavior of the primary constituent device.
```
```swift
```swift
```swift
var primaryConstituentDeviceSwitchingBehavior: AVCaptureDevice.PrimaryConstituentDeviceSwitchingBehavior
```
```

The switching behavior for the primary constituent device.
```
```swift
```swift
```swift
var primaryConstituentDeviceRestrictedSwitchingBehaviorConditions: AVCaptureDevice.PrimaryConstituentDeviceRestrictedSwitchingBehaviorConditions
```
```

The conditions that restrict the primary constituent device’s switching behavior.
```
```swift
```swift
```swift
var activePrimaryConstituentDeviceSwitchingBehavior: AVCaptureDevice.PrimaryConstituentDeviceSwitchingBehavior
```
```

The switching behavior of the active constituent device.
```
```swift
```swift
```swift
var activePrimaryConstituentDeviceRestrictedSwitchingBehaviorConditions: AVCaptureDevice.PrimaryConstituentDeviceRestrictedSwitchingBehaviorConditions
```
```

The conditions that restrict camera switching behavior for the active primary constituent device.
```
```swift
```swift
```swift
var activePrimaryConstituent: AVCaptureDevice?
```
```

A virtual device’s active primary constituent device.
```
```swift
```swift
```swift
enum PrimaryConstituentDeviceSwitchingBehavior
```
```

Constants that control when to allow a virtual device to switch its active primary constituent device.
```
```swift
```swift
```swift
struct PrimaryConstituentDeviceRestrictedSwitchingBehaviorConditions
```
```

A structure that defines the conditions in which to restrict camera switching.
```
```swift
```swift
```swift
var supportedFallbackPrimaryConstituentDevices: [AVCaptureDevice]
```
```

The constituent devices available to select as a fallback for a longer focal length primary constituent device.
```
```swift
```swift
```swift
var fallbackPrimaryConstituentDevices: [AVCaptureDevice]
```
```

The fallback devices to use when a constituent device with a longer focal length becomes limited by its light sensitivity or minimum focus distance.
```
```

### [Configuring macOS Features](/documentation/AVFoundation/AVCaptureDevice#Configuring-macOS-Features)

[

API Reference

macOS Capture Features](/documentation/avfoundation/macos-capture-features)

Control the transport behavior and input sources of capture hardware in macOS.

### [Accessing Camera Extrinsics](/documentation/AVFoundation/AVCaptureDevice#Accessing-Camera-Extrinsics)

```swift
```swift
```swift
```swift
class func extrinsicMatrix(from: AVCaptureDevice, to: AVCaptureDevice) -> Data?
```
```

Returns the relative extrinsic matrix from one capture device to another.
```
```

### [Determining Lens Stabilization](/documentation/AVFoundation/AVCaptureDevice#Determining-Lens-Stabilization)

```swift
```swift
```swift
```swift
enum LensStabilizationStatus
```
```

Constants that indicate the status of optical image stabilization hardware during a bracketed photo capture.
```
```

### [Instance Properties](/documentation/AVFoundation/AVCaptureDevice#Instance-Properties)

```swift
```swift
```swift
```swift
var cameraLensSmudgeDetectionInterval: CMTime
```
```
Beta
```
```swift
```swift
```swift
var cameraLensSmudgeDetectionStatus: AVCaptureCameraLensSmudgeDetectionStatus
```
```
Beta
```
```swift
```swift
```swift
var cinematicVideoCaptureSceneMonitoringStatuses: Set<AVCaptureSceneMonitoringStatus>
```
```
Beta
```
```swift
```swift
```swift
var exposureRectOfInterest: CGRect
```
```
Beta
```
```swift
```swift
```swift
var focusRectOfInterest: CGRect
```
```
Beta
```
```swift
```swift
```swift
var isCameraLensSmudgeDetectionEnabled: Bool
```
```
Beta
```
```swift
```swift
```swift
var isExposureRectOfInterestSupported: Bool
```
```
Beta
```
```swift
```swift
```swift
var isFocusRectOfInterestSupported: Bool
```
```
Beta
```
```swift
```swift
```swift
var minExposureRectOfInterestSize: CGSize
```
```
Beta
```
```swift
```swift
```swift
var minFocusRectOfInterestSize: CGSize
```
```
Beta
```
```swift
```swift
```swift
var nominalFocalLengthIn35mmFilm: Float
```
```

The nominal 35mm equivalent focal length of the capture device’s lens.

Beta
```
```

### [Instance Methods](/documentation/AVFoundation/AVCaptureDevice#Instance-Methods)

```swift
```swift
```swift
```swift
func defaultRectForExposurePoint(ofInterest: CGPoint) -> CGRect
```
```
Beta
```
```swift
```swift
```swift
func defaultRectForFocusPoint(ofInterest: CGPoint) -> CGRect
```
```
Beta
```
```swift
```swift
```swift
func setCameraLensSmudgeDetectionEnabled(Bool, detectionInterval: CMTime)
```
```
Beta
```
```swift
```swift
```swift
func setCinematicVideoFixedFocus(at: CGPoint, focusMode: AVCaptureDevice.CinematicVideoFocusMode)
```
```
Beta
```
```swift
```swift
```swift
func setCinematicVideoTrackingFocus(at: CGPoint, focusMode: AVCaptureDevice.CinematicVideoFocusMode)
```
```
Beta
```
```swift
```swift
```swift
func setCinematicVideoTrackingFocus(detectedObjectID: Int, focusMode: AVCaptureDevice.CinematicVideoFocusMode)
```
```
Beta
```
```

### [Enumerations](/documentation/AVFoundation/AVCaptureDevice#Enumerations)

```swift
```swift
```swift
```swift
enum CinematicVideoFocusMode
```
```
Beta
```
```

## [Relationships](/documentation/AVFoundation/AVCaptureDevice#relationships)

### [Inherits From](/documentation/AVFoundation/AVCaptureDevice#inherits-from)

*   [`NSObject`](/documentation/ObjectiveC/NSObject-swift.class)

### [Conforms To](/documentation/AVFoundation/AVCaptureDevice#conforms-to)

*   [`CVarArg`](/documentation/Swift/CVarArg)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)

## [See Also](/documentation/AVFoundation/AVCaptureDevice#see-also)

### [Capture devices](/documentation/AVFoundation/AVCaptureDevice#Capture-devices)

[

Choosing a Capture Device](/documentation/avfoundation/choosing-a-capture-device)

Select the front or back camera, or use advanced features like the TrueDepth camera or dual camera.

```swift
```swift
```swift
class AVCaptureDeviceInput
```
```

An object that provides media input from a capture device to a capture session.
```
```swift
```swift
```swift
class AVContinuityDevice
```
```

A class that represents a physical iOS device that’s nearby and can provide access to its cameras and microphones.
```
```swift
```swift
```swift
class AVExternalStorageDevice
```
```

Represents a physical external storage device that stores media assets.
```
```swift
```swift
```swift
class AVExternalStorageDeviceDiscoverySession
```
```

Informs your app when the external storage devices connect to and disconnect from the system.
```