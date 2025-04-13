

- AVFoundation
- AVCaptureVideoDataOutput
-  availableVideoCodecTypes 

Instance Property

# availableVideoCodecTypes

The video codecs that the output supports.

iOS 5.0+iPadOS 5.0+Mac Catalyst 14.0+macOS 10.7+tvOS 17.0+

``` source
var availableVideoCodecTypes: [AVVideoCodecType] { get }
```

## Discussion

The value contains an array of video codecs that the output supports. Specify the codec it uses by setting a supported value for the AVVideoCodecKey entry in its videoSettings dictionary. The first format in the returned list is the most efficient output format.

## See Also

### Retrieving Supported Video Types

var availableVideoPixelFormatTypes: [OSType]

The video pixel formats the output supports.

func availableVideoCodecTypesForAssetWriter(writingTo: AVFileType) -> [AVVideoCodecType]

The video codecs that the output supports for writing video to the output file.

struct AVVideoCodecType

A set of constants that describe the codecs the system supports for video capture.

