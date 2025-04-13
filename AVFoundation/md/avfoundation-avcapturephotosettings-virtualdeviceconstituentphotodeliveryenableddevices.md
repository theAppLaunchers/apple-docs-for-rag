

- AVFoundation
- AVCapturePhotoSettings
-  virtualDeviceConstituentPhotoDeliveryEnabledDevices 

Instance Property

# virtualDeviceConstituentPhotoDeliveryEnabledDevices

The constituent devices for which the virtual device should deliver photos.

iOS 13.0+iPadOS 13.0+Mac Catalyst 14.0+tvOS 17.0+

``` source
var virtualDeviceConstituentPhotoDeliveryEnabledDevices: [AVCaptureDevice] { get set }
```

## Discussion

You can opt in to constituent-device photo delivery by setting this property to any subset of the devices in the virtual device’s constituentDevices array. The framework calls your photoOutput(_:didFinishProcessingPhoto:error:)callback once for each of the devices you include in the array.

You may only set this property to a non-`nil` array if you’ve set your photo output’s isVirtualDeviceConstituentPhotoDeliveryEnabled property to true, and your delegate implements the photoOutput(_:didFinishProcessingPhoto:error:) method.

The default value of this property is an empty array.

## See Also

### Configuring photo settings

var flashMode: AVCaptureDevice.FlashMode

A setting for whether to fire the flash when capturing photos.

var isAutoRedEyeReductionEnabled: Bool

A Boolean value that indicates whether to use auto red-eye reduction on flash captures.

var maxPhotoDimensions: CMVideoDimensions

The maximum resolution of the photo to capture.

var photoQualityPrioritization: AVCapturePhotoOutput.QualityPrioritization

A setting that indicates how to prioritize photo quality against speed of photo delivery.

var isCameraCalibrationDataDeliveryEnabled: Bool

A Boolean value that determines whether a dual photo capture also delivers camera calibration data.

var isAutoContentAwareDistortionCorrectionEnabled: Bool

A Boolean value that specifies whether the photo output, at its discretion, uses content-aware distortion correction on this photo request.

var isAutoVirtualDeviceFusionEnabled: Bool

A Boolean value that specifies whether to use automatic virtual-device image fusion.

var isDualCameraDualPhotoDeliveryEnabled: Bool

A Boolean value that determines whether a dual camera device delivers images from both cameras.

Deprecated

var isAutoDualCameraFusionEnabled: Bool

A Boolean value that specifies whether captures automatically combine data from a dual camera device.

Deprecated

var isAutoStillImageStabilizationEnabled: Bool

A Boolean value that specifies whether captures use automatic image stabilization.

Deprecated

var isHighResolutionPhotoEnabled: Bool

A Boolean value that specifies whether to capture still images at the highest resolution supported by the active device and format.

Deprecated

