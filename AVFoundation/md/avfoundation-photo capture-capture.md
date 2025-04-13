

- AVFoundation
-  Photo capture 

API Collection

# Photo capture

Capture high-quality still images, Live Photos, and supporting photo data.

## Topics

### Photo capture

Capturing consistent color images

Add the power of a photography studio and lighting rig to your app with the new Constant Color API.

Capturing Still and Live Photos

Configure and capture single or multiple still images, Live Photos, and other forms of photography.

Capturing Photos in RAW and Apple ProRAW Formats

Support professional photography workflows by enabling minimally processed image capture in your camera app.

Supporting Continuity Camera in Your Mac App

Incorporate scanned documents and pictures from a user’s iPhone, iPad, or iPod touch into your Mac app using Continuity Camera.

class AVCapturePhoto

A container for image data from a photo capture output.

class AVCaptureDeferredPhotoProxy

A lightly-processed photo with data that the system may use to process and fetch a higher-resolution asset at a later time.

class AVCapturePhotoOutput

A capture output for still image, Live Photos, and other photography workflows.

protocol AVCapturePhotoCaptureDelegate

Methods for monitoring progress and receiving results from a photo capture output.

class AVCapturePhotoOutputReadinessCoordinator

An object that monitors changes to a photo output’s capture readiness.

protocol AVCapturePhotoOutputReadinessCoordinatorDelegate

A delegate protocol to receive updates about a photo output’s capture readiness.

class AVCaptureStillImageOutput

A capture output for capturing still photos.

Deprecated

### Photo settings

class AVCapturePhotoSettings

A specification of the features and settings to use for a single photo capture request.

class AVCapturePhotoBracketSettings

A specification of the features and settings to use for a photo capture request that captures multiple images with varied settings.

class AVCaptureResolvedPhotoSettings

A description of the features and settings in use for an in-progress or complete photo capture request.

### Matte data

class AVPortraitEffectsMatte

An auxiliary image used to separate foreground from background with high resolution.

class AVSemanticSegmentationMatte

An object that wraps a matting image for a particular semantic segmentation.

## See Also

### Capture

Capture setup

Configure built-in cameras and microphones, and external capture devices, for media capture.

Audio and video capture

Capture audio and video directly to media files, or capture streams of media for direct access to media sample buffers.

Additional data capture

Capture additional data including depth and metadata, and synchronize capture from multiple outputs.

