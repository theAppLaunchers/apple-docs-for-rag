

- Core Image
- CIFaceFeature
-  trackingID 

Instance Property

# trackingID

The tracking identifier of the face object.

iOS 5.0+iPadOS 5.0+Mac Catalyst 13.1+macOS 10.7+tvOS 9.0+visionOS 1.0+

``` source
var trackingID: Int32 { get }
```

## Discussion

Core Image provides a tracking identifier for faces it detects in a video stream, which you can use to identify when a `CIFaceFeature` objects detected in one video frame is the same face detected in a previous video frame.

This identifier persists only as long as a face is in the frame and is not associated with a specific face. In other words, if a face moves out of the video frame and comes back into the frame later, another ID is assigned. (Core Image detects faces, but does not recognize specific faces.)

## See Also

### Tracking Distinct Faces in Video

var hasTrackingID: Bool

A Boolean value that indicates whether the face object has a tracking ID.

var hasTrackingFrameCount: Bool

A Boolean value that indicates the face object has a tracking frame count.

var trackingFrameCount: Int32

The tracking frame count of the face.

