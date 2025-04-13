

- AVFoundation
- AVCapturePhotoSettings
-  metadata 

Instance Property

# metadata

A dictionary of metadata keys and values to embed in photo file output.

iOS 11.0+iPadOS 11.0+Mac Catalyst 14.0+tvOS 17.0+

``` source
var metadata: [String : Any] { get set }
```

## Discussion

The capture output automatically writes metadata including image orientation, EXIF camera properties, and Live Photo metadata, but you can override those values or specify additional metadata using the keys and values listed in `CGImageProperties`. (Setting this property with any other keys raises an exception.)

