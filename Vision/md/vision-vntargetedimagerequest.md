

- Vision
-  VNTargetedImageRequest 

Class

# VNTargetedImageRequest

The abstract superclass for image analysis requests that operate on both the processed image and a secondary image.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+macOS 10.13+tvOS 11.0+visionOS 1.0+

``` source
class VNTargetedImageRequest
```

## Overview

Other Vision request handlers that operate on both the processed image and a secondary image inherit from this abstract base class. Instantiate one of its subclasses to perform image analysis, and pass in auxiliary image data by filling in the `options` dictionary at initialization.

## Topics

### Creating a Request

init(targetedCGImage: CGImage, options: [VNImageOption : Any], completionHandler: VNRequestCompletionHandler?)

Creates a new request targeting a Core Graphics image, executing the completion handler when done.

init(targetedCGImage: CGImage, orientation: CGImagePropertyOrientation, options: [VNImageOption : Any], completionHandler: VNRequestCompletionHandler?)

Creates a new request targeting a Core Graphics image of known orientation, executing the completion handler when done.

init(targetedCIImage: CIImage, options: [VNImageOption : Any], completionHandler: VNRequestCompletionHandler?)

Creates a new request targeting a Core Image image.

init(targetedCIImage: CIImage, orientation: CGImagePropertyOrientation, options: [VNImageOption : Any], completionHandler: VNRequestCompletionHandler?)

Creates a new request targeting a Core Image image of known orientation, executing the completion handler when done.

init(targetedCVPixelBuffer: CVPixelBuffer, options: [VNImageOption : Any], completionHandler: VNRequestCompletionHandler?)

Creates a new request targeting an image in a pixel buffer.

init(targetedCVPixelBuffer: CVPixelBuffer, orientation: CGImagePropertyOrientation, options: [VNImageOption : Any], completionHandler: VNRequestCompletionHandler?)

Creates a new request targeting an image in a pixel buffer of known orientation.

init(targetedCMSampleBuffer: CMSampleBuffer, options: [VNImageOption : Any], completionHandler: VNRequestCompletionHandler?)

Creates a new request with a completion handler that targets an image in a sample buffer.

init(targetedCMSampleBuffer: CMSampleBuffer, orientation: CGImagePropertyOrientation, options: [VNImageOption : Any], completionHandler: VNRequestCompletionHandler?)

Creates a new request with a completion handler that targets an image of a known orientation in a sample buffer.

init(targetedImageData: Data, options: [VNImageOption : Any], completionHandler: VNRequestCompletionHandler?)

Creates a new request targeting an image as raw data, executing the completion handler when done.

init(targetedImageData: Data, orientation: CGImagePropertyOrientation, options: [VNImageOption : Any], completionHandler: VNRequestCompletionHandler?)

Creates a new request targeting a raw data image of known orientation, executing the completion handler when done.

init(targetedImageURL: URL, options: [VNImageOption : Any], completionHandler: VNRequestCompletionHandler?)

Creates a new request targeting an image at the specified URL, executing the completion handler when done.

init(targetedImageURL: URL, orientation: CGImagePropertyOrientation, options: [VNImageOption : Any], completionHandler: VNRequestCompletionHandler?)

Creates a new request targeting an image of known orientation, at the specified URL, executing the completion handler when done.

## Relationships

### Inherits From

- VNImageBasedRequest

### Inherited By

- VNGenerateOpticalFlowRequest
- VNImageRegistrationRequest

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSCopying
- NSObjectProtocol

## See Also

### Image alignment

Aligning Similar Images

Construct a composite image from images that capture the same scene.

class VNImageRegistrationRequest

The abstract superclass for image-analysis requests that align images according to their content.

class VNTranslationalImageRegistrationRequest

An image-analysis request that determines the affine transform necessary to align the content of two images.

class VNTrackTranslationalImageRegistrationRequest

An image-analysis request, as a stateful request you track over time, that determines the affine transform necessary to align the content of two images.

class VNHomographicImageRegistrationRequest

An image-analysis request that determines the perspective warp matrix necessary to align the content of two images.

class VNTrackHomographicImageRegistrationRequest

An image-analysis request, as a stateful request you track over time, that determines the perspective warp matrix necessary to align the content of two images.

class VNImageAlignmentObservation

The abstract superclass for image-analysis results that describe the relative alignment of two images.

class VNImageTranslationAlignmentObservation

Affine transform information that an image-alignment request produces.

class VNImageHomographicAlignmentObservation

An object that represents a perspective warp transformation.

