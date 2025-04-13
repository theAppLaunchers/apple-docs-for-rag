

- UIKit
-  UISaveVideoAtPathToSavedPhotosAlbum(\_:\_:\_:\_:) 

Function

# UISaveVideoAtPathToSavedPhotosAlbum(\_:\_:\_:\_:)

Adds the movie from the specified path to the user’s Camera Roll album.

iOS 3.1+iPadOS 3.1+Mac Catalyst 13.1+visionOS 1.0+

``` source
func UISaveVideoAtPathToSavedPhotosAlbum(
    _ videoPath: String,
    _ completionTarget: Any?,
    _ completionSelector: Selector?,
    _ contextInfo: UnsafeMutableRawPointer?
)
```

## Parameters 

`videoPath`  

The filesystem path to the movie file you want to save to the Camera Roll album.

`completionTarget`  

Optionally, the object whose selector the system calls after it writes the movie to the Camera Roll album.

`completionSelector`  

The method selector of the `completionTarget` object to call. Make this optional method conform to the following signature:

```
// Swift
func video(_ videoPath: String?,
           didFinishSavingWithError error: Error?,
           contextInfo: UnsafeMutableRawPointer?) {}
```

```
// Objective-C
- (void)video: (NSString *) videoPath
    didFinishSavingWithError: (NSError *) error
              contextInfo: (void *) contextInfo;
```

`contextInfo`  

An optional pointer to any context-specific data that you want the system to pass to the completion selector.

## Discussion

When you use this function with an image picker controller, you’d typically call it within your imagePickerController(_:didFinishPickingMediaWithInfo:) delegate method implementation.

Before calling this function, call the UIVideoAtPathIsCompatibleWithSavedPhotosAlbum(_:) function to determine if it’s possible to save movies to the Camera Roll album. For a code example, refer to Camera Programming Topics for iOS.

The use of the `completionTarget`, `completionSelector`, and `contextInfo` parameters is optional and necessary only if you want to receive an asynchronous notification when the function finishes writing the movie to the user’s Camera Roll or Saved Photos album. If you don’t want to receive a notification, pass `nil` for these parameters.

When an iOS device without a camera uses it, this method adds the movie to the Saved Photos album rather than to the Camera Roll album.

## See Also

### Photo album

func UIImageWriteToSavedPhotosAlbum(UIImage, Any?, Selector?, UnsafeMutableRawPointer?)

Adds the specified image to the user’s Camera Roll album.

func UIVideoAtPathIsCompatibleWithSavedPhotosAlbum(String) -> Bool

Returns a Boolean value that indicates whether the specified video is compatible to save to the user’s Camera Roll album.

