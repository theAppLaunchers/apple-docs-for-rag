

- Vision
- VNImageRequestHandler
-  init(cmSampleBuffer:depthData:orientation:options:) 

Initializer

# init(cmSampleBuffer:depthData:orientation:options:)

Creates a request handler that performs requests on an image in a sample buffer that contains depth data.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+

``` source
init(
    cmSampleBuffer sampleBuffer: CMSampleBuffer,
    depthData: AVDepthData,
    orientation: CGImagePropertyOrientation,
    options: [VNImageOption : Any] = [:]
)
```

## Parameters 

`sampleBuffer`  

The sample buffer that contains the image to analyze. If the sample buffer doesn’t contain an image buffer with image data, the system raises an error.

`depthData`  

The depth data to associate with the image.

`orientation`  

The EXIF orientation of the image.

`options`  

A dictionary that specifies auxiliary information about the image.

## Discussion

Sample buffers may contain metadata, like the camera intrinsics. Vision algorithms that support this metadata use it in their analysis, unless overwritten by the options you specify.

Important

Use a physical device to perform your testing. Performing requests in Simulator may produce inaccurate results due to the inability of Core Image to render certain pixel formats in this environment.

## See Also

### Creating a Request Handler

init(cgImage: CGImage, options: [VNImageOption : Any])

Creates a handler to be used for performing requests on Core Graphics images.

init(cgImage: CGImage, orientation: CGImagePropertyOrientation, options: [VNImageOption : Any])

Creates a handler to be used for performing requests on a Core Graphics image with known orientation.

init(ciImage: CIImage, options: [VNImageOption : Any])

Creates a handler to use for performing requests on Core Image image data.

init(ciImage: CIImage, orientation: CGImagePropertyOrientation, options: [VNImageOption : Any])

Creates a handler to be used for performing requests on Core Image image data of a known orientation.

init(cvPixelBuffer: CVPixelBuffer, options: [VNImageOption : Any])

Creates a handler for performing requests on a Core Video pixel buffer.

init(cvPixelBuffer: CVPixelBuffer, orientation: CGImagePropertyOrientation, options: [VNImageOption : Any])

Creates a handler for performing requests on a Core Video pixel buffer of a known orientation.

init(cvPixelBuffer: CVPixelBuffer, depthData: AVDepthData, orientation: CGImagePropertyOrientation, options: [VNImageOption : Any])

init(cmSampleBuffer: CMSampleBuffer, options: [VNImageOption : Any])

Creates a request handler that performs requests on an image contained within a sample buffer.

init(cmSampleBuffer: CMSampleBuffer, orientation: CGImagePropertyOrientation, options: [VNImageOption : Any])

Creates a request handler that performs requests on an image of a specified orientation contained within a sample buffer.

init(data: Data, options: [VNImageOption : Any])

Creates a handler to use for performing requests on an image in a data object.

init(data: Data, orientation: CGImagePropertyOrientation, options: [VNImageOption : Any])

Creates a handler to use for performing requests on an image of known orientation.

init(url: URL, options: [VNImageOption : Any])

Creates a handler to be used for performing requests on an image at the specified URL.

init(url: URL, orientation: CGImagePropertyOrientation, options: [VNImageOption : Any])

Creates a handler to be used for performing requests on an image with known orientation, at the specified URL.

