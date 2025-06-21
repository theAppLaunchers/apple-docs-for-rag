Framework

# Vision

Apply computer vision algorithms to perform a variety of tasks on input images and videos.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.0+macOS 10.13+tvOS 11.0+visionOS 1.0+

## [Overview](/documentation/Vision#overview)

The Vision framework combines machine learning technologies and Swift’s concurrency features to perform computer vision tasks in your app. Use the Vision framework to analyze images for a variety of purposes:

*   Tracking human and animal body poses or the trajectory of an object
    
*   Recognizing text in 18 different languages
    
*   Detecting faces and face landmarks, such as eyes, nose, and mouth
    
*   Performing hand tracking to enable new device interactions
    
*   Calculating an aesthetics score to determine how memorable a photo is
    

![An illustration showing a dog, and a magnifying glass depicting the dog being analyzed.](https://docs-assets.developer.apple.com/published/c745ff2988bec9749a8ba2313d77598e/vision-framework%402x.png)

To begin using the framework, you create a request for the type of analysis you want to do. Each request conforms to the [`VisionRequest`](/documentation/vision/visionrequest) protocol. You then perform the request to get an observation object — or an array of observations — with the analysis details for the request. There are more than 25 requests available to choose from. Vision also allows the use of custom Core ML models for tasks like classification or object detection.

Note

Starting in iOS 18.0, the Vision framework provides a new Swift-only API. See [Original Objective-C and Swift API](/documentation/vision/original-objective-c-and-swift-api) to view the original API.

## [Topics](/documentation/Vision#topics)

### [Still-image analysis](/documentation/Vision#Still-image-analysis)

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
struct DetectLensSmudgeRequest
```
```

A request that detects a smudge on a lens from an image or video frame capture.

Beta
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

### [Image sequence analysis](/documentation/Vision#Image-sequence-analysis)

```swift
```swift
```swift
```swift
class GeneratePersonSegmentationRequest
```
```

A request that produces a matte image for a person it finds in the input image.
```
```swift
```swift
```swift
struct GeneratePersonInstanceMaskRequest
```
```

A request that produces a mask of individual people it finds in the input image.
```
```swift
```swift
```swift
struct DetectDocumentSegmentationRequest
```
```

A request that detects rectangular regions that contain text in the input image.
```
```swift
```swift
```swift
protocol StatefulRequest
```
```

The protocol for a type that builds evidence of a condition over time.
```
```

### [Image aesthetics analysis](/documentation/Vision#Image-aesthetics-analysis)

[

Generating high-quality thumbnails from videos](/documentation/vision/generating-thumbnails-from-videos)

Identify the most visually pleasing frames in a video by using the image-aesthetics scores request.

```swift
```swift
```swift
struct CalculateImageAestheticsScoresRequest
```
```

A request that analyzes an image for aesthetically pleasing attributes.
```

### [Saliency analysis](/documentation/Vision#Saliency-analysis)

```swift
```swift
```swift
```swift
struct GenerateAttentionBasedSaliencyImageRequest
```
```

An object that produces a heat map that identifies the parts of an image most likely to draw attention.
```
```swift
```swift
```swift
struct GenerateObjectnessBasedSaliencyImageRequest
```
```

A request that generates a heat map that identifies the parts of an image most likely to represent objects.
```
```

### [Object tracking](/documentation/Vision#Object-tracking)

```swift
```swift
```swift
```swift
class TrackObjectRequest
```
```

An image-analysis request that tracks the movement of a previously identified object across multiple images or video frames.
```
```swift
```swift
```swift
class TrackRectangleRequest
```
```

An image-analysis request that tracks movement of a previously identified rectangular object across multiple images or video frames.
```
```

### [Face and body detection](/documentation/Vision#Face-and-body-detection)

[

Analyzing a selfie and visualizing its content](/documentation/vision/analyzing-a-selfie-and-visualizing-its-content)

Calculate face-capture quality and visualize facial features for a collection of images using the Vision framework.

```swift
```swift
```swift
struct DetectFaceRectanglesRequest
```
```

A request that finds faces within an image.
```
```swift
```swift
```swift
struct DetectFaceLandmarksRequest
```
```

An image-analysis request that finds facial features like eyes and mouth in an image.
```
```swift
```swift
```swift
struct DetectFaceCaptureQualityRequest
```
```

A request that produces a floating-point number that represents the capture quality of a face in a photo.
```
```swift
```swift
```swift
struct DetectHumanRectanglesRequest
```
```

A request that finds rectangular regions that contain people in an image.
```

### [Body and hand pose detection](/documentation/Vision#Body-and-hand-pose-detection)

```swift
```swift
```swift
```swift
struct DetectHumanBodyPoseRequest
```
```

A request that detects a human body pose.
```
```swift
```swift
```swift
struct DetectHumanHandPoseRequest
```
```

A request that detects a human hand pose.
```
```swift
```swift
```swift
protocol PoseProviding
```
```

An observation that provides a collection of joints that make up a pose.
```
```swift
```swift
```swift
enum Chirality
```
```

The hand sidedness of a pose.
```
```swift
```swift
```swift
struct Joint
```
```

A pose joint represented as a normalized point in an image, along with a label and a confidence value.
```
```

### [3D body pose detection](/documentation/Vision#3D-body-pose-detection)

```swift
```swift
```swift
```swift
class DetectHumanBodyPose3DRequest
```
```

A request that detects points on human bodies in 3D space, relative to the camera.
```
```swift
```swift
```swift
struct Joint3D
```
```

An object that represents a body pose joint in 3D space.
```
```

### [Text detection](/documentation/Vision#Text-detection)

[

Recognizing tables within a document](/documentation/vision/recognize-tables-within-a-document)

Scan a document containing a contact table and extract the content within the table in a formatted way.

[

Locating and displaying recognized text](/documentation/vision/locating-and-displaying-recognized-text)

Perform text recognition on a photo using the Vision framework’s text-recognition request.

```swift
```swift
```swift
struct RecognizeDocumentsRequest
```
```

An image-analysis request to scan an image of a document and provide information about its structure.

Beta
```
```swift
```swift
```swift
struct DocumentObservation
```
```

Information about the sections of content that an image-analysis request detects in a document.

Beta
```
```swift
```swift
```swift
struct DetectTextRectanglesRequest
```
```

An image-analysis request that finds regions of visible text in an image.
```
```swift
```swift
```swift
struct RecognizeTextRequest
```
```

An image-analysis request that recognizes text in an image.
```

### [Barcode detection](/documentation/Vision#Barcode-detection)

```swift
```swift
```swift
```swift
struct DetectBarcodesRequest
```
```

A request that detects barcodes in an image.
```
```

### [Trajectory, contour, and horizon detection](/documentation/Vision#Trajectory-contour-and-horizon-detection)

```swift
```swift
```swift
```swift
class DetectTrajectoriesRequest
```
```

A request that detects the trajectories of shapes moving along a parabolic path.
```
```swift
```swift
```swift
struct DetectContoursRequest
```
```

A request that detects the contours of the edges of an image.
```
```swift
```swift
```swift
struct DetectHorizonRequest
```
```

An image-analysis request that determines the horizon angle in an image.
```
```

### [Animal detection](/documentation/Vision#Animal-detection)

```swift
```swift
```swift
```swift
struct DetectAnimalBodyPoseRequest
```
```

A request that detects an animal body pose.
```
```swift
```swift
```swift
struct RecognizeAnimalsRequest
```
```

A request that recognizes animals in an image.
```
```

### [Optical flow and rectangle detection](/documentation/Vision#Optical-flow-and-rectangle-detection)

```swift
```swift
```swift
```swift
class TrackOpticalFlowRequest
```
```

A request that determines the direction change of vectors for each pixel from a previous to current image.
```
```swift
```swift
```swift
struct DetectRectanglesRequest
```
```

An image-analysis request that finds projected rectangular regions in an image.
```
```

### [Image alignment](/documentation/Vision#Image-alignment)

```swift
```swift
```swift
```swift
class TrackTranslationalImageRegistrationRequest
```
```

An image-analysis request that you track over time to determine the affine transform necessary to align the content of two images.
```
```swift
```swift
```swift
class TrackHomographicImageRegistrationRequest
```
```

An image-analysis request that you track over time to determine the perspective warp matrix necessary to align the content of two images.
```
```swift
```swift
```swift
protocol TargetedRequest
```
```

A type for analyzing two images together.
```
```

### [Image feature print and background removal](/documentation/Vision#Image-feature-print-and-background-removal)

```swift
```swift
```swift
```swift
struct GenerateImageFeaturePrintRequest
```
```

An image-based request to generate feature prints from an image.
```
```swift
```swift
```swift
struct GenerateForegroundInstanceMaskRequest
```
```

A request that generates an instance mask of noticeable objects to separate from the background.
```
```

### [Machine learning image analysis](/documentation/Vision#Machine-learning-image-analysis)

```swift
```swift
```swift
```swift
struct CoreMLRequest
```
```

An image-analysis request that uses a Core ML model to process images.
```
```swift
```swift
```swift
struct CoreMLFeatureValueObservation
```
```

An object that represents a collection of key-value information that a Core ML image-analysis request produces.
```
```swift
```swift
```swift
struct ClassificationObservation
```
```

An object that represents classification information that an image-analysis request produces.
```
```swift
```swift
```swift
struct PixelBufferObservation
```
```

An object that represents an image that an image-analysis request produces.
```
```

### [Image locations and regions](/documentation/Vision#Image-locations-and-regions)

```swift
```swift
```swift
```swift
struct NormalizedPoint
```
```

A point in a 2D coordinate system.
```
```swift
```swift
```swift
struct NormalizedRect
```
```

The location and dimensions of a rectangle.
```
```swift
```swift
```swift
typealias NormalizedRegion
```
```

A polygon composed of normalized points.

Beta
```
```swift
```swift
```swift
struct NormalizedCircle
```
```

The center point and radius of a 2D circle.
```
```swift
```swift
```swift
protocol BoundingBoxProviding
```
```

A protocol for objects that have a bounding box.
```
```swift
```swift
```swift
protocol BoundingRegionProviding
```
```

A protocol for objects that have a defined boundary in an image.

Beta
```
```swift
```swift
```swift
protocol QuadrilateralProviding
```
```

A protocol for objects that have a bounding quadrilateral.
```
```swift
```swift
```swift
enum CoordinateOrigin
```
```

The origin of a coordinate system relative to an image.
```
```

### [Request Handlers](/documentation/Vision#Request-Handlers)

```swift
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
class TargetedImageRequestHandler
```
```

An object that performs image-analysis requests on two images.
```
```

### [Utilities](/documentation/Vision#Utilities)

```swift
```swift
```swift
```swift
enum ComputeStage
```
```

Types that represent the compute stage.
```
```swift
```swift
```swift
class VideoProcessor
```
```

An object that performs offline analysis of video content.
```
```

### [Errors](/documentation/Vision#Errors)

```swift
```swift
```swift
```swift
enum VisionError
```
```

The errors that the framework produces.
```
```

### [Legacy API](/documentation/Vision#Legacy-API)

[

API Reference

Original Objective-C and Swift API](/documentation/vision/original-objective-c-and-swift-api)