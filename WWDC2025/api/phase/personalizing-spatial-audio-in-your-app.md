*   [PHASE](/documentation/phase)
*   Personalizing spatial audio in your app

Article

# Personalizing spatial audio in your app

Enhance the realism of spatial audio output by tracking a person’s head movement and accounting for their personal spatial audio profile.

iOS 18.0+iPadOS 18.0+macOS 15.0+tvOS 18.0+

## [Overview](/documentation/PHASE/personalizing-spatial-audio-in-your-app#Overview)

Apps that implement 3D spatial audio in supported frameworks can fine tune the listener experience by automatically updating the listener orientation according to a person’s head movement while wearing compatible AirPods, and using the personal spatial audio profile that they create in Settings.

In iOS 18, iPadOS 18, and tvOS 18, the system adds spatial audio effects for games by default, and offers a Control Center toggle to control the effect. If your game implements custom spatial audio, you need to disable the effect to prevent undesirable artifacts from spatializing an audio stream twice, an effect known as _double spatialization_.

## [Apply a personal spatial audio profile](/documentation/PHASE/personalizing-spatial-audio-in-your-app#Apply-a-personal-spatial-audio-profile)

A person can opt in to _personalized spatial audio_ by creating a profile in settings that walks them through scanning their head using the camera on their iPhone. The system constructs a geometric representation of the shape of the person’s head that supporting audio frameworks observe to enhance the simulation of sound traveling through the physical environment.

When you add the [`com.apple.developer.spatial-audio.profile-access`](/documentation/BundleResources/Entitlements/com.apple.developer.spatial-audio.profile-access) entitlement to your app and implement custom spatial audio with either of the following frameworks, the system automatically takes the personal spatial audio profile into account as it tailors the audio output:

*   [`AUSpatialMixer Parameters`](/documentation/audiotoolbox/1390073-auspatialmixer_parameters) (in Audio Toolbox)
    
*   [`AVAudioEngine`](/documentation/AVFAudio/AVAudioEngine)
    
*   [PHASE](/documentation/PHASE)
    

## [Enable head tracking with compatible AirPods](/documentation/PHASE/personalizing-spatial-audio-in-your-app#Enable-head-tracking-with-compatible-AirPods)

Head tracking adjusts the orientation of the listener according to their head movement while wearing compatible AirPods. This creates the effect that the listener is present in the 3D scene. Head tracking works by simulating the effect of detaching the left and right speakers from the person’s head and virtually placing them in stationary positions in the physical environment, to the left and right of the person, respectively.

To enable head tracking:

*   Add the [`com.apple.developer.coremotion.head-pose`](/documentation/BundleResources/Entitlements/com.apple.developer.coremotion.head-pose) entitlement to your app.
    
*   Configure the API to opt in; the process varies depending on the framework:
    

`AVAudioEngine`

Adjust the [`AVAudioEnvironmentNode`](/documentation/AVFAudio/AVAudioEnvironmentNode) orientation to match the person’s head pose by setting the [`isListenerHeadTrackingEnabled`](/documentation/AVFAudio/AVAudioEnvironmentNode/isListenerHeadTrackingEnabled) property to `true`.

PHASE

Adjust the [`PHASEListener`](/documentation/PHASE/PHASEListener) orientation by setting the [`automaticHeadTrackingFlags`](/documentation/PHASE/PHASEListener/automaticHeadTrackingFlags) property to [`orientation`](/documentation/PHASE/PHASEAutomaticHeadTrackingFlags/orientation).

Audio Toolbox

Adjust the `AUSpatialMixer` orientation to match the person’s head pose by setting the [`kAudioUnitProperty_SpatialMixerEnableHeadTracking`](/documentation/AudioToolbox/kAudioUnitProperty_SpatialMixerEnableHeadTracking) property to `true`.

## [Disable the system-provided spatial audio](/documentation/PHASE/personalizing-spatial-audio-in-your-app#Disable-the-system-provided-spatial-audio)

In iOS 18, iPadOS 18, and tvOS 18, the system adds an automatic spatial audio effect for apps in the App Store Connect game category when a person wears compatible AirPods. If your game already implements spatial audio with one of the supporting frameworks or third-party engine, you need to disable the automatic effect by adding the [`AVGameBypassSystemSpatialAudio`](/documentation/BundleResources/Information-Property-List/AVGameBypassSystemSpatialAudio) key to your app’s `Info.plist` file.

Automatic spatial audio works by adding a reverb to the room and simulating the effect of detaching the left and right speakers from the person’s head. The speakers’ output from a virtual position at a fixed length in front of the person, with a short distance between the left and right outputs.

Control Center provides UI to toggle this effect and the feature is on by default. If you opt out with the `AVGameBypassSystemSpatialAudio` key, the system disables the effect and Control Center toggle.

## [See Also](/documentation/PHASE/personalizing-spatial-audio-in-your-app#see-also)

### [Essentials](/documentation/PHASE/personalizing-spatial-audio-in-your-app#Essentials)

[

Playing sound from a location in a 3D scene](/documentation/phase/playing-sound-from-a-location-in-a-3d-scene)

Position sound from a specific direction and automatically raise or lower volume based on the environment.

[

PHASE updates](/documentation/Updates/PHASE)

Learn about important changes to PHASE.