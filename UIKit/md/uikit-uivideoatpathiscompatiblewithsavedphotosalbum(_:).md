

- UIKit
-  UIVideoAtPathIsCompatibleWithSavedPhotosAlbum(\_:) 

Function

# UIVideoAtPathIsCompatibleWithSavedPhotosAlbum(\_:)

Returns a Boolean value that indicates whether the specified video is compatible to save to the user’s Camera Roll album.

iOS 3.1+iPadOS 3.1+Mac Catalyst 13.1+visionOS 1.0+

``` source
func UIVideoAtPathIsCompatibleWithSavedPhotosAlbum(_ videoPath: String) -> Bool
```

## Parameters 

`videoPath`  

The filesystem path to the movie file you want to save.

## Return Value

true if the video can be saved to the Camera Roll album or false if it cannot.

## Discussion

Not all devices are able to play video files placed in the user’s Camera Roll album. Before attempting to save a video, call this function and check its return value to ensure that saving the video is supported for the current device. For a code example, refer to Camera Programming Topics for iOS.

When used on an iOS device without a camera, this method indicates whether the specified movie can be saved to the Saved Photos album rather than to the Camera Roll album.

## See Also

### Photo album

func UIImageWriteToSavedPhotosAlbum(UIImage, Any?, Selector?, UnsafeMutableRawPointer?)

Adds the specified image to the user’s Camera Roll album.

func UISaveVideoAtPathToSavedPhotosAlbum(String, Any?, Selector?, UnsafeMutableRawPointer?)

Adds the movie from the specified path to the user’s Camera Roll album.

