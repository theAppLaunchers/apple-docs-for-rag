Framework

# DockKit

Interact with accessories that track subjects on camera as they move around.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+

## [Overview](/documentation/DockKit#Overview)

DockKit interfaces with DockKit-compatible motorized stands known as dock accessories to track the location of objects that appear in video frames. It determines how to best position the iPhone camera to frame and track objects, with improved person tracking using combined body and face tracking for human subjects. This feature, known as _system tracking_, automatically starts as soon as a person docks iPhone onto a compatible motorized stand and launches the Camera app. For example, system tracking is useful for content creators who want the camera to follow them while they move around their space, or instructors on a video call who are walking around a classroom.

![iPhone mounted in landscape orientation on a dock accessory with its back facing outward. A cocentric circle near the camera indicates that it is active.](https://docs-assets.developer.apple.com/published/790e7a21e706ee6445e00e2d6d12bdb3/dock%402x.png)

Dock

![iPhone mounted in landscape orientation on a dock accessory with its back facing outward. An arc around the base of the dock accessory indicates horizontal movement. An arc around the body of iPhone indicates up and down movement.](https://docs-assets.developer.apple.com/published/d3211312df3276762f7038d194067169/move%402x.png)

Move

![iPhone mounted in landscape orientation on a dock accessory with the back of the iPhone aimed at a person in a video frame. The person in the frame is in midair, in the process of jumping.](https://docs-assets.developer.apple.com/published/15cbb5e75993a385ce4167d291e2ca80/track%402x.png)

Track

You can disable system tracking and implement your own tracking behavior by using [`DockAccessoryManager`](/documentation/dockkit/dockaccessorymanager) and [`DockAccessory`](/documentation/dockkit/dockaccessory). Implement your own tracking behavior to follow a location of a custom object such as a pet, or a pair of hands performing a task. DockKit accessories integrate with [`AVCaptureSession`](/documentation/AVFoundation/AVCaptureSession) so apps with camera permissions work seamlessly together.

## [Topics](/documentation/DockKit#topics)

### [Controlling the dock accessory](/documentation/DockKit#Controlling-the-dock-accessory)

[

Controlling a DockKit accessory using your camera app](/documentation/dockkit/controlling-a-dockkit-accessory-using-your-camera-app)

Follow subjects in real time using an iPhone that you mount on a DockKit accessory.

```swift
```swift
```swift
class DockAccessoryManager
```
```

Observe the state of dock accessories and enable or disable system tracking.
```
```swift
```swift
```swift
class DockAccessory
```
```

Obtain accessory information and control tracking behavior.
```
```swift
```swift
```swift
enum DockKitError
```
```

A list of errors that DockKit sends.
```

### [Customizing tracking behavior](/documentation/DockKit#Customizing-tracking-behavior)

[

Modify rotation and positioning programmatically](/documentation/dockkit/modify-rotation-and-positioning-behavior-programmatically)

Perform custom control of the dock accessory.

[

Track custom objects in a frame](/documentation/dockkit/track-custom-objects-in-a-frame)

Use your machine learning model to focus on a specific subject.