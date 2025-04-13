

- AVKit
- AVPictureInPictureController
-  init(playerLayer:) 

Initializer

# init(playerLayer:)

Creates a Picture in Picture controller with a player layer.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.15+tvOS 14.0+visionOS 1.0+

``` source
convenience init?(playerLayer: AVPlayerLayer)
```

## Parameters 

`playerLayer`  

The player layer from which to source the media content for the Picture in Picture controller.

## Discussion

For Picture in Picture to work correctly, maintain a strong reference to this object whether your app is running in the foreground or background.

Important

Before attempting to create a controller instance, verify that the current device supports Picture in Picture by calling the isPictureInPictureSupported() class method. Attempting to create a Picture in Picture controller on an unsupported device returns `nil`.

## See Also

### Creating a Controller

init(contentSource: AVPictureInPictureController.ContentSource)

Creates a Picture in Picture controller with a content source.

