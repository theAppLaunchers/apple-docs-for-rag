

- AVFoundation
- AVCapturePhotoCaptureDelegate
-  photoOutput(\_:didFinishProcessingPhoto:previewPhoto:resolvedSettings:bracketSettings:error:) Deprecated

Instance Method

# photoOutput(\_:didFinishProcessingPhoto:previewPhoto:resolvedSettings:bracketSettings:error:)

Provides the delegate a captured image in a processed format (such as JPEG).

iOS 10.0–11.0DeprecatediPadOS 10.0–11.0DeprecatedMac Catalyst 13.1–13.1Deprecated

``` source
optional func photoOutput(
    _ output: AVCapturePhotoOutput,
    didFinishProcessingPhoto photoSampleBuffer: CMSampleBuffer?,
    previewPhoto previewPhotoSampleBuffer: CMSampleBuffer?,
    resolvedSettings: AVCaptureResolvedPhotoSettings,
    bracketSettings: AVCaptureBracketedStillImageSettings?,
    error: (any Error)?
)
```

Deprecated

In iOS 11 and later, implement the photoOutput(_:didFinishProcessingPhoto:error:) method instead.

## Parameters 

`output`  

The photo output performing the capture.

`photoSampleBuffer`  

A sample buffer containing the captured photo, either as uncompressed pixel buffer or compressed image data (see the format property of your photo settings object), along with timing information and other metadata.

If an error prevented successful capture, this parameter is `nil`—see the `error` parameter for a description of the failure.

`previewPhotoSampleBuffer`  

If you requested a thumbnail-sized version of the photo (with the previewPhotoFormat property of your photo settings object), a sample buffer containing the thumbnail photo in the requested format. If you did not request preview delivery, or if an error prevented capture, this parameter is `nil`.

`resolvedSettings`  

An object describing the settings used for this capture. Match this object’s uniqueID value to the uniqueID property of the photo settings object you initiated capture with to determine which capture request this delegate call corresponds to. You can also use this object to find out which values the photo output has chosen for automatic settings.

`bracketSettings`  

If you requested a bracketed capture of multiple images with a AVCapturePhotoBracketSettings, a bracketed still image settings object describing which image in the bracket this delegate call corresponds to. If you did not request bracketed capture, this parameter is `nil`.

`error`  

If an the capture process could not proceed successfully, an error object describing the failure; otherwise, `nil`.

## Discussion

Use this method to receive the results of photo capture in a processed format such as JPEG. (If you request capture in both RAW and a processed format, the photo output calls both this method and the photoOutput(_:didFinishProcessingRawPhoto:previewPhoto:resolvedSettings:bracketSettings:error:) method.)

Important

You must implement either this method or the photoOutput(_:didFinishProcessingPhoto:error:) method if you request capture in a processed format. The photo output validates this requirement when you call its capturePhoto(with:delegate:) method; if your delegate does not implement the correct methods, the photo output raises an exception.

If you request capture in a processed format, the photo output calls this method once for each exposure in the capture request. If you request a single image capture, this method is called once. If you request a bracketed capture with multiple exposures, this method is called once for each exposure.

## See Also

### Receiving Capture Results

func photoOutput(AVCapturePhotoOutput, didFinishProcessingPhoto: AVCapturePhoto, error: (any Error)?)

Provides the delegate with the captured image and associated metadata resulting from a photo capture.

func photoOutput(AVCapturePhotoOutput, didFinishRecordingLivePhotoMovieForEventualFileAt: URL, resolvedSettings: AVCaptureResolvedPhotoSettings)

Notifies the delegate that the movie content of a Live Photo has finished recording.

func photoOutput(AVCapturePhotoOutput, didFinishProcessingLivePhotoToMovieFileAt: URL, duration: CMTime, photoDisplayTime: CMTime, resolvedSettings: AVCaptureResolvedPhotoSettings, error: (any Error)?)

Provides the delegate the movie file URL resulting from a Live Photo capture.

func photoOutput(AVCapturePhotoOutput, didFinishCapturingDeferredPhotoProxy: AVCaptureDeferredPhotoProxy?, error: (any Error)?)

Tells the delegate when the system finishes capturing the photo proxy.

func photoOutput(AVCapturePhotoOutput, didFinishProcessingRawPhoto: CMSampleBuffer?, previewPhoto: CMSampleBuffer?, resolvedSettings: AVCaptureResolvedPhotoSettings, bracketSettings: AVCaptureBracketedStillImageSettings?, error: (any Error)?)

Provides the delegate a captured image in RAW format.

Deprecated

