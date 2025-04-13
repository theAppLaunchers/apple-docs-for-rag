

- ARKit
- ARSession
-  Recording and Replaying AR Session Data 

Article

# Recording and Replaying AR Session Data

Record an AR session in Reality Composer and replay it in your ARKit app.

## Overview

ARKit apps use video feeds and sensor data from an iOS device to understand the world around the device. This reliance on real-world input makes the testing of an AR experience challenging because real-world input is never the same across two AR sessions. Differences in lighting conditions, device motion, and the location of nearby objects all change how RealityKit understands and renders the scene each time.

To provide consistent data to your AR app, you can record a session using Reality Composer, then use the recorded camera and sensor data to drive your app when running from Xcode.

### Record an AR Session in Reality Composer

On an iOS device, create a Reality Composer scene with the same anchor type as the app you’re recording the session for, then follow these steps to create the recording.

1.  Tap the Settings toolbar button. It’s the circle containing three dots in the upper-right corner.

2.  In the Settings sidebar that appears, tap Developer.

3.  In the Developer window, tap Record AR Session.

4.  Move your iOS device to the initial location for your recording.

5.  Tap the record button to start.

Move your device around until it anchors the Reality Composer scene, then continue moving it around until you’ve captured the desired input. When done, tap the stop button to end recording. Rename the recording by providing a custom name in the Capture Complete window, then tap Done to save the recording to Reality Composer’s library.

### Replay an AR Session in Reality Composer

To replay a session capture right after recording it, tap the Replay button in the Capture Complete window.

To replay a session later, follow these steps:

1.  Tap the Settings toolbar button.

2.  Tap Developer in the Settings inspector.

3.  In the Developer window, tap Replay AR\_ \_Session.

4.  Select the session to replay.

5.  Press the Play button to begin playback.

If the recorded session meets your needs, you can export it to a Quicktime movie file by hitting the Share button from either the Recording Complete window or the Playback Complete window. If your Mac is on and unlocked, you can Airdrop the file directly to your computer.

### Use a Recorded Session in an App

In Xcode, you can specify an exported recording to use when launching your app. To select a recording, edit your project’s scheme and choose the Run phase from the left pane. Select the Options tab, then look for a row labeled ARKit with a “Replay data” checkbox next to it. Check that box, then choose Add Replay Data to Project from the popup button next to it to select the recording.

When you run your app with this option selected, it uses the recorded session instead of the device’s camera and sensors.

## See Also

### Saving or sharing state

func getCurrentWorldMap(completionHandler: (ARWorldMap?, (any Error)?) -> Void)

Returns an object encapsulating the world-tracking session’s space-mapping state and set of anchors.

