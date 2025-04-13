

- ARKit
-  Verifying Device Support and User Permission 

Article

# Verifying Device Support and User Permission

Check whether your app can use ARKit and respect user privacy at runtime.

## Overview

ARKit requires iOS 11.0 or later and an iOS device with an A9 or later processor. Some ARKit features require later iOS versions or specific devices. ARKit also uses a device camera, so you need to configure iOS privacy controls so the user can permit camera access for your app.

How to handle device compatibility support depends on how your app uses ARKit:

- **If the basic functionality of your app requires AR (using the back camera):** Add the `arkit` key in the UIRequiredDeviceCapabilities section of your app’s `Info.plist` file. Using this key makes your app available only to ARKit-compatible devices.

- **If augmented reality is a secondary feature of your app:** Check for whether the current device supports the AR configuration you want to use by testing the isSupported property of the appropriate ARConfiguration subclass.

- **If your app uses face-tracking AR:** Face tracking requires the front-facing TrueDepth camera on iPhone X. Your app remains available on other devices, so you must test the ARFaceTrackingConfiguration.isSupported property to determine face-tracking support on the current device.

Tip

Check the isSupported property before offering AR features in your app’s UI, so that users on unsupported devices aren’t disappointed by trying to access those features.

### Handle User Consent and Privacy

For your app to use ARKit, the user must explicitly grant your app permission for camera access. ARKit automatically asks the user for permission the first time your app runs an AR session.

iOS requires your app to provide a static message to be displayed when the system asks for camera or microphone permission. Your app’s `Info.plist` file must include the NSCameraUsageDescription key. For that key, provide text that explains why your app needs camera access so that the user can feel confident granting permission to your app.

Note

If you create a new ARKit app using the Xcode template, a default camera usage description is provided for you.

If your app uses ARFaceTrackingConfiguration, ARKit provides your app with personal facial information. If you use ARKit face tracking features, your app must include a privacy policy describing to users how you intend to use face tracking and face data. For details, see the Apple Developer Program License Agreement.

## See Also

### iOS

class ARSession

The object that manages the major tasks associated with every AR experience, such as motion tracking, camera passthrough, and image analysis.

class ARAnchor

An object that specifies the position and orientation of an item in the physical environment.

ARKit in iOS

Integrate iOS device camera and motion features to produce augmented reality experiences in your app or game.

