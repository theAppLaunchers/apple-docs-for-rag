

- AVFoundation
- AVCapturePhotoSettings
-  livePhotoMovieFileURL 

Instance Property

# livePhotoMovieFileURL

A URL at which to write Live Photo movie output.

iOS 10.0+iPadOS 10.0+Mac Catalyst 14.0+tvOS 17.0+

``` source
var livePhotoMovieFileURL: URL? { get set }
```

## Discussion

Live Photos capture both a still image and a short movie, which the system presents together in user interfaces such as the Photos app. By default, this property’s value is `nil`, disabling Live Photo capture. Set this property to a file URL to capture Live Photos.

When you enable Live Photo capture, the following requirements apply:

- The photo output’s isLivePhotoCaptureEnabled property must be true, and its and isLivePhotoCaptureSuspended property must be false.

- The URL you specify must be a file URL to an accessible location in your app’s sandbox.

- Your delegate object must implement the photoOutput(_:didFinishProcessingLivePhotoToMovieFileAt:duration:photoDisplayTime:resolvedSettings:error:) method.

The capture output validates these requirements when you call the capturePhoto(with:delegate:) method. If your settings and delegate don’t meet these requirements, that method raises an exception.

## See Also

### Configuring Live Photo Settings

var livePhotoMovieMetadata: [AVMetadataItem]!

A dictionary of metadata to include in the Live Photo movie file.

var livePhotoVideoCodecType: AVVideoCodecType

The video codec to use for encoding the movie portion of Live Photo output.

