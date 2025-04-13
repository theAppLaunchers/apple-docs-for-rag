

- Bundle Resources
- Information Property List
-  UIPreferredDefaultInterfaceOrientation 

Property List Key

# UIPreferredDefaultInterfaceOrientation

A string that indicates the preferred initial interface orientation for iPad and iPhone apps running on visionOS.

iOS 2.0+iPadOS 2.0+

## Details 

Type  

string

## Possible Values 

`UIInterfaceOrientationPortrait`  

`UIInterfaceOrientationPortraitUpsideDown`  

`UIInterfaceOrientationLandscapeLeft`  

`UIInterfaceOrientationLandscapeRight`  

## Discussion

When compatible iPad and iPhone apps run on visionOS, the system references this key to determine the preferred initial interface orientation for the content that appears in a window in the person’s surroundings. This key is optional, and applications that don’t provide a value receive a default interface orientation that the system provides. The system evaluates the key, but might use a different value. For example, if a pre-existing state exists, that state defines the interface orientation. If a preferred interface orientation doesn’t exist in the app’s UISupportedInterfaceOrientations, the app receives a default interface orientation provided by the system – landscape right for iPad apps, portrait for iPhone apps.

Note

This key doesn’t apply to app’s built against the visionOS SDK.

## See Also

### Orientation

UIInterfaceOrientation

The initial orientation of the app’s user interface.

**Name:** Initial interface orientation

UISupportedInterfaceOrientations

The interface orientations supported by your app.

**Name:** Supported interface orientations

