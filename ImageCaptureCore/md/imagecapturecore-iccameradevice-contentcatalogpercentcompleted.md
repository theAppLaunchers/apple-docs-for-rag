

- ImageCaptureCore
- ICCameraDevice
-  contentCatalogPercentCompleted 

Instance Property

# contentCatalogPercentCompleted

The percentage of the camera’s content that has been catalogued.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+macOS 10.4+visionOS 1.0+

``` source
var contentCatalogPercentCompleted: Int { get }
```

## Discussion

The value of this property ranges from 0 to 100.

## See Also

### Reading Files

var contents: [ICCameraItem]?

All image, movie, and audio files stored on the camera, in an order that reflects the camera’s storage folder structure.

var mediaFiles: [ICCameraItem]?

All image, movie and audio files stored on the camera, without regard to the camera’s storage folder structure.

func files(ofType: String) -> [String]?

Returns an array of files of the selected type on the camera.

func requestReadData(from: ICCameraFile, atOffset: off_t, length: off_t, readDelegate: Any, didReadDataSelector: Selector, contextInfo: UnsafeMutableRawPointer?)

Asynchronously reads data of a specified length from a specified offset.

