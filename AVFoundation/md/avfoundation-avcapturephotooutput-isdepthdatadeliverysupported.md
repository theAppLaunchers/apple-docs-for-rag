

- AVFoundation
- AVCapturePhotoOutput
-  isDepthDataDeliverySupported 

Instance Property

# isDepthDataDeliverySupported

A Boolean value indicating whether the capture output currently supports depth data capture.

iOS 11.0+iPadOS 11.0+Mac Catalyst 14.0+tvOS 17.0+

``` source
var isDepthDataDeliverySupported: Bool { get }
```

## Discussion

Depth data captures a per-pixel map of scene depth information delivered alongside the photo image and optionally embedded in image file output. Depth data can be used for purposes such as applying depth-sensitive photo filter effects (like that seen in the iOS Camera app’s Portrait mode) and performing computer vision tasks.

Not all devices and capture formats support depth capture. This property’s value can change if the sessionPreset property of the current capture session or the activeFormat property of the underlying capture device changes. If a camera or format change causes this property’s value to become false, the isDepthDataDeliveryEnabled property’s value also becomes false.

This property is key-value observable.

## See Also

### Configuring Depth Data Capture

var isDepthDataDeliveryEnabled: Bool

A Boolean value that specifies whether to configure the capture pipeline for depth data capture.

