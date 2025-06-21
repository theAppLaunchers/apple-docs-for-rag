*   [Vision](/documentation/vision)
*   DetectLensSmudgeRequest Beta

Structure

# DetectLensSmudgeRequest

A request that detects a smudge on a lens from an image or video frame capture.

iOS 26.0+BetaiPadOS 26.0+BetaMac Catalyst 26.0+BetamacOS 26.0+BetatvOS 26.0+BetavisionOS 26.0+Beta

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
struct DetectLensSmudgeRequest
```
```
```
```
```
```
```
```

## [Overview](/documentation/Vision/DetectLensSmudgeRequest#overview)

Use this request to detect whether an image or video is captured with a smudged lens. A smudge is anything that obscures a lens, like a fingerprint or raindrops, resulting in a hazy or blurry capture. Use this capability to find the best frame from a video or set of images.

![A clear image of poppies in a field.](https://docs-assets.developer.apple.com/published/a2182d46ae002806e283ee7e36a5932e/detect-lens-smudge-overview-clear%402x.png)

Clear image

![A hazy image of poppies in a field.](https://docs-assets.developer.apple.com/published/a7e9c231f72215bb56f5383e9fe0421f/detect-lens-smudge-overview-obscured%402x.png)

Smudged image

Perform this request when detecting a smudge within an image or video frame. The request returns a [`SmudgeObservation`](/documentation/vision/smudgeobservation). This observation contains a floating-point [`confidence`](/documentation/vision/smudgeobservation/confidence) value in the range of `0.0` to `1.0` indicating the probability that a capture has an impaired or smudged lens at capture time. A score of `1.0` represents a high probability the lens is smudged at capture time.

Running [`DetectLensSmudgeRequest`](/documentation/vision/detectlenssmudgerequest) requires a device with A14 Bionic and later or device with M1 and later.

Note

Certain types of content may be categorized as a smudge, such as naturally-blurred objects, long exposure, and motion blur while taking a photo. Make sure that you are using a request on a fixed capture where the device is stable when taking the image.

To use the properties of the request, add a [`ImageProcessingRequest`](/documentation/vision/imageprocessingrequest) to your chosen capture type.

```swift
```swift
```swift
```swift
```swift
```swift
func isGoodCapture(imageURL:URL) async throws -> Bool {
```
```
   
   // Set an optional threshold from 0.0 to 1.0 to flag a maximum level of smudge in your capture.
    let smudgeThreshold: Float = 0.9;
    let request = DetectLensSmudgeRequest(.revision1)
    let smudgeObservation = try await request.perform(on: imageURL)
    
    return (smudgeObservation.confidence < smudgeThreshold)
}
```
```
```
```

## [Topics](/documentation/Vision/DetectLensSmudgeRequest#topics)

### [Creating a request](/documentation/Vision/DetectLensSmudgeRequest#Creating-a-request)

[`init(DetectLensSmudgeRequest.Revision?)`](/documentation/vision/detectlenssmudgerequest/init\(_:\))

Creates a request to detect whether the camera lens has a smudge.

### [Getting the revision](/documentation/Vision/DetectLensSmudgeRequest#Getting-the-revision)

```swift
```swift
```swift
```swift
let revision: DetectLensSmudgeRequest.Revision
```
```

The algorithm or implementation the request uses.
```

[`static var supportedRevisions: [DetectLensSmudgeRequest.Revision]`](/documentation/vision/detectlenssmudgerequest/supportedrevisions)

The collection of revisions the request supports.

```swift
```swift
```swift
enum Revision
```
```

A type that describes the algorithm or implementation that the request performs.
```
```

### [Inspecting a request](/documentation/Vision/DetectLensSmudgeRequest#Inspecting-a-request)

```swift
```swift
```swift
```swift
var cropAndScaleAction: ImageCropAndScaleAction
```
```

An optional setting that tells the algorithm how to scale an input image before generating the result.
```
```swift
```swift
```swift
enum ImageCropAndScaleAction
```
```

A scale to apply to an input image before performing a request.
```
```

### [Performing a request](/documentation/Vision/DetectLensSmudgeRequest#Performing-a-request)

```swift
```swift
```swift
```swift
func perform(on: URL, orientation: CGImagePropertyOrientation?) async throws -> Self.Result
```
```

Performs the request on an image URL and produces observations.

**Required** Default implementations provided.
```
```swift
```swift
```swift
func perform(on: Data, orientation: CGImagePropertyOrientation?) async throws -> Self.Result
```
```

Performs the request on image data and produces observations.

**Required** Default implementations provided.
```
```swift
```swift
```swift
func perform(on: CGImage, orientation: CGImagePropertyOrientation?) async throws -> Self.Result
```
```

Performs the request on a Core Graphics image and produces observations.

**Required** Default implementations provided.
```
```swift
```swift
```swift
func perform(on: CVPixelBuffer, orientation: CGImagePropertyOrientation?) async throws -> Self.Result
```
```

Performs the request on a pixel buffer and produces observations.

**Required** Default implementations provided.
```
```swift
```swift
```swift
func perform(on: CMSampleBuffer, orientation: CGImagePropertyOrientation?) async throws -> Self.Result
```
```

Performs the request on a Core Media buffer and produces observations.

**Required** Default implementations provided.
```
```swift
```swift
```swift
func perform(on: CIImage, orientation: CGImagePropertyOrientation?) async throws -> Self.Result
```
```

Performs the request on a Core Image image and produces observations.

**Required** Default implementations provided.
```
```swift
```swift
```swift
struct SmudgeObservation
```
```

An observation that provides an overall score of the presence of a smudge in an image or video frame capture.
```
```

## [Relationships](/documentation/Vision/DetectLensSmudgeRequest#relationships)

### [Conforms To](/documentation/Vision/DetectLensSmudgeRequest#conforms-to)

*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`ImageProcessingRequest`](/documentation/vision/imageprocessingrequest)
*   [`Sendable`](/documentation/Swift/Sendable)
*   [`SendableMetatype`](/documentation/Swift/SendableMetatype)
*   [`VisionRequest`](/documentation/vision/visionrequest)

## [See Also](/documentation/Vision/DetectLensSmudgeRequest#see-also)

### [Still-image analysis](/documentation/Vision/DetectLensSmudgeRequest#Still-image-analysis)

[

Classifying images for categorization and search](/documentation/vision/classifying-images-for-categorization-and-search)

Analyze and label images using a Vision classification request.

```swift
```swift
```swift
struct ClassifyImageRequest
```
```

A request to classify an image.
```
```swift
```swift
```swift
protocol ImageProcessingRequest
```
```

A type for image-analysis requests that focus on a specific part of an image.
```
```swift
```swift
```swift
class ImageRequestHandler
```
```

An object that processes one or more image-analysis requests pertaining to a single image.
```
```swift
```swift
```swift
protocol VisionRequest
```
```

A type for image-analysis requests.
```
```swift
```swift
```swift
protocol VisionObservation
```
```

A type for objects produced by image-analysis requests.
```
```swift
```swift
```swift
struct SmudgeObservation
```
```

An observation that provides an overall score of the presence of a smudge in an image or video frame capture.

Beta
```

Beta Software

This documentation contains preliminary information about an API or technology in development. This information is subject to change, and software implemented according to this documentation should be tested with final operating system software.

[Learn more about using Apple's beta software](https://developer.apple.com/support/beta-software/)