

- AVFoundation
-  AVDepthData 

Class

# AVDepthData

A container for per-pixel distance or disparity information captured by compatible camera devices.

iOS 11.0+iPadOS 11.0+Mac Catalyst 14.0+macOS 10.13+tvOS 11.0+visionOS 1.0+

``` source
class AVDepthData
```

## Mentioned in 

Extracting Portrait Effects Matte Image Data from a Photo

Creating Auxiliary Depth Data Manually

## Overview

*Depth data* is a generic term for a map of per-pixel data containing depth-related information. A depth data object wraps a disparity or depth map and provides conversion methods, focus information, and camera calibration data to aid in using the map for rendering or computer vision tasks.

A depth map describes at each pixel the distance to an object, in meters.

A disparity map describes normalized shift values for use in comparing two images. The value for each pixel in the map is in units of 1/meters: (`pixelShift / (pixelFocalLength * baselineInMeters)`).

The capture pipeline generates disparity or depth maps from camera images containing nonrectilinear data. Camera lenses have small imperfections that cause small distortions in their resultant images compared to an ideal pinhole camera model, so AVDepthData maps contain nonrectilinear (nondistortion-corrected) data as well. The maps’ values are warped to match the lens distortion characteristics present in the YUV image pixel buffers captured at the same time.

Because a depth data map is nonrectilinear, you can use an AVDepthData map as a proxy for depth when rendering effects to its accompanying image, but not to correlate points in 3D space. To use depth data for computer vision tasks, use the data in the cameraCalibrationData property to rectify the depth data.

There are two ways to capture depth data:

- The AVCaptureDepthDataOutput class captures and delivers depth data in a stream (similar to how the AVCaptureVideoDataOutput delivers video data).

- The AVCapturePhotoOutput class delivers depth data as a property of an AVCapturePhoto object containing the captured image.

You can also create AVDepthData objects using information obtained from image files with the Image I/O framework.

When editing images containing depth information, use the methods listed in Transforming and Processing to generate derivative AVDepthData objects reflecting the edits that have been performed.

## Topics

### Creating Depth Data

convenience init(fromDictionaryRepresentation: [AnyHashable : Any]) throws

Creates a depth data object from depth information such as that found in an image file.

func dictionaryRepresentation(forAuxiliaryDataType: AutoreleasingUnsafeMutablePointer&lt;NSString?>?) -> [AnyHashable : Any]?

Returns a dictionary representation of the depth data suitable for writing into an image file.

### Reading Pixel Depth Information

var depthDataMap: CVPixelBuffer

A pixel buffer containing the depth data’s per-pixel depth or disparity data map.

var depthDataType: OSType

The pixel format of the depth data map.

### Evaluating Depth Data

var isDepthDataFiltered: Bool

A Boolean value indicating whether the depth map contains temporally smoothed data.

var depthDataAccuracy: AVDepthData.Accuracy

The general accuracy of depth data map values.

enum Accuracy

Values indicating the general accuracy of a depth data map.

var depthDataQuality: AVDepthData.Quality

The overall quality of the depth map.

enum Quality

Values indicating the overall quality of a depth data map.

### Transforming and Processing

func applyingExifOrientation(CGImagePropertyOrientation) -> Self

Returns a derivative depth data object by mirroring or rotating it to the specified orientation.

func converting(toDepthDataType: OSType) -> Self

Returns a derivative depth data object by converting the depth data map to the specified data type.

var availableDepthDataTypes: [OSType]

The list of depth data formats to which you can convert this depth data.

func replacingDepthDataMap(with: CVPixelBuffer) throws -> Self

Returns a derivative depth data object by replacing the depth data map.

### Using Calibration Data

var cameraCalibrationData: AVCameraCalibrationData?

The imaging parameters with which this depth data was captured.

## Relationships

### Inherits From

- NSObject

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSObjectProtocol

## See Also

### Depth data capture

Capturing Photos with Depth

Get a depth map with a photo to create effects like the system camera’s Portrait mode (on compatible devices).

Creating Auxiliary Depth Data Manually

Generate a depth image and attach it to your own image.

Capturing depth using the LiDAR camera

Access the LiDAR camera on supporting devices to capture precise depth data.

AVCamFilter: Applying Filters to a Capture Stream

Render a capture stream with rose-colored filtering and depth effects.

Streaming Depth Data from the TrueDepth Camera

Visualize depth data in 2D and 3D from the TrueDepth camera.

Enhancing Live Video by Leveraging TrueDepth Camera Data

Apply your own background to a live capture feed streamed from the front-facing TrueDepth camera.

class AVCaptureDepthDataOutput

A capture output that records scene depth information on compatible camera devices.

class AVCameraCalibrationData

Information about the camera characteristics used to capture images and depth data.

