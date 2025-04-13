

- DockKit
-  Track custom objects in a frame 

Article

# Track custom objects in a frame

Use your machine learning model to focus on a specific subject.

## Overview

You can use your own custom machine learning model, also known as *inference*. This allows DockKit to track a custom subject, such as a dog or a cat. Once you’ve applied your machine learning model on a set of video frames, use DockKit to generate and provide tracking vectors.

## Obtain video images

Begin by obtaining images from the video capture source.

```
captureOutput(_ output: AVCaptureOutput, didOutput sampleBuffer: CMSampleBuffer, from connection: AVCaptureConnection)

let pixelBuffer = CMSampleBufferGetImageBuffer(sampleBuffer)
```

## Provide observations

Once you’ve passed your video frames to your custom machine learning model, supply these observations to the accessory using track(_:cameraInformation:).

```
let cameraInfo = DockAccessory.CameraInformation(captureDevice: cameraDevice!.deviceType, cameraPosition: cameraDevice!.position, orientation: .LandscapeRight, cameraIntrinsics: self.intrinsics, referenceDimensions: self.referenceDimensions)
let obs = DockAccessory.Observation(identifier: 0, type: .humanFace, rect: rect, faceYawAngle: Measurement(value: self.faceYaw, unit: UnitAngle.radians))
let observations = [obs]

try await dockAccessory.track(observations, cameraInformation: cameraInfo)
```

Format the output of your object detections as an array of DockAccessory.Observation objects. If you want to write your own custom tracking logic, or generate your own position and velocity-based vectors, see Modify rotation and positioning programmatically.

Call track(_:cameraInformation:) at an interval between 10 and 30 times per second. When calling this method , the tracking system analyzes the subjects and determines which one to focus on and how to frame it. The tracking vector derives from these two choices, and the accessory keeps the subjects framed appropriately.

The tracking vector arrives at the accessory which controls the motors. This work occurs in the background and can take some time to complete.

In some cases, the call to track(_:cameraInformation:) might not generate a vector, or the vector may only keep the accessory at rest.

## See Also

### Customizing tracking behavior

Modify rotation and positioning programmatically

Perform custom control of the dock accessory.

