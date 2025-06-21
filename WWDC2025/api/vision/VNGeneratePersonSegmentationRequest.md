*   [Vision](/documentation/vision)
*   VNGeneratePersonSegmentationRequest

Class

# VNGeneratePersonSegmentationRequest

An object that produces a matte image for a person it finds in the input image.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
class VNGeneratePersonSegmentationRequest
```
```
```
```
```
```
```
```

## [Overview](/documentation/Vision/VNGeneratePersonSegmentationRequest#overview)

Perform this request to detect and generate an image mask for a person in an image. The request returns the resulting image mask in an instance of [`VNPixelBufferObservation`](/documentation/vision/vnpixelbufferobservation).

## [Topics](/documentation/Vision/VNGeneratePersonSegmentationRequest#topics)

### [Creating a Request](/documentation/Vision/VNGeneratePersonSegmentationRequest#Creating-a-Request)

[`init()`](/documentation/vision/vngeneratepersonsegmentationrequest/init\(\))

Creates a generate person segmentation request.

[`init(completionHandler: VNRequestCompletionHandler?)`](/documentation/vision/vngeneratepersonsegmentationrequest/init\(completionhandler:\))

Creates a generate person segmentation request with a completion handler.

### [Configuring the Request](/documentation/Vision/VNGeneratePersonSegmentationRequest#Configuring-the-Request)

```swift
```swift
```swift
```swift
var outputPixelFormat: OSType
```
```

The pixel format of the output image.
```
```swift
```swift
```swift
var qualityLevel: VNGeneratePersonSegmentationRequest.QualityLevel
```
```

A value that indicates how the request balances accuracy and performance.
```
```swift
```swift
```swift
enum QualityLevel
```
```

Constants that define the levels of quality for a person segmentation request.
```
```

### [Accessing the Results](/documentation/Vision/VNGeneratePersonSegmentationRequest#Accessing-the-Results)

```swift
```swift
```swift
```swift
var results: [VNPixelBufferObservation]?
```
```

The results of the segmentation request.
```
```swift
```swift
```swift
class VNPixelBufferObservation
```
```

An object that represents an image that an image-analysis request produces.
```
```

### [Identifying Request Revisions](/documentation/Vision/VNGeneratePersonSegmentationRequest#Identifying-Request-Revisions)

```swift
```swift
```swift
```swift
let VNGeneratePersonSegmentationRequestRevision1: Int
```
```

A constant for specifying revision 1 of the person segmentation generation request.
```
```

### [Instance Methods](/documentation/Vision/VNGeneratePersonSegmentationRequest#Instance-Methods)

```swift
```swift
```swift
```swift
func supportedOutputPixelFormats() throws -> [NSNumber]
```
```

Returns a list of output pixel formats that the request supports.
```
```

## [Relationships](/documentation/Vision/VNGeneratePersonSegmentationRequest#relationships)

### [Inherits From](/documentation/Vision/VNGeneratePersonSegmentationRequest#inherits-from)

*   [`VNStatefulRequest`](/documentation/vision/vnstatefulrequest)

### [Conforms To](/documentation/Vision/VNGeneratePersonSegmentationRequest#conforms-to)

*   [`CVarArg`](/documentation/Swift/CVarArg)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`NSCopying`](/documentation/Foundation/NSCopying)
*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)

## [See Also](/documentation/Vision/VNGeneratePersonSegmentationRequest#see-also)

### [Image sequence analysis](/documentation/Vision/VNGeneratePersonSegmentationRequest#Image-sequence-analysis)

[

Applying Matte Effects to People in Images and Video](/documentation/vision/applying-matte-effects-to-people-in-images-and-video)

Generate image masks for people automatically by using semantic person-segmentation.

[

Detecting Human Actions in a Live Video Feed](/documentation/createml/detecting_human_actions_in_a_live_video_feed)

Identify body movements by sending a person’s pose data from a series of video frames to an action-classification model.

[

Segmenting and colorizing individuals from a surrounding scene](/documentation/vision/segmenting-and-colorizing-individuals-from-a-surrounding-scene)

Use the Vision framework to isolate and apply colors to people in an image.

```swift
```swift
```swift
class VNStatefulRequest
```
```

An abstract request type that builds evidence of a condition over time.
```
```swift
```swift
```swift
class VNGeneratePersonInstanceMaskRequest
```
```

An object that produces a mask of individual people it finds in the input image.
```
```swift
```swift
```swift
class VNDetectDocumentSegmentationRequest
```
```

An object that detects rectangular regions that contain text in the input image.
```
```swift
```swift
```swift
class VNSequenceRequestHandler
```
```

An object that processes image-analysis requests for each frame in a sequence.
```