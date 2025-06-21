*   [Audio Toolbox](/documentation/audiotoolbox)
*   Anchoring sound to a window or volume

Article

# Anchoring sound to a window or volume

Provide unique app experiences by attaching sounds to windows and volumes in 3D space.

## [Overview](/documentation/AudioToolbox/spatializing-sound-from-a-uiscene#Overview)

Many audio playback APIs have a property to configure their 3D spatial rendering using the [`SpatialAudioExperience`](/documentation/audiotoolbox/spatialaudioexperience) type [`HeadTrackedSpatialAudio`](/documentation/audiotoolbox/headtrackedspatialaudio). This article shows how to take advantage of [`HeadTrackedSpatialAudio`](/documentation/audiotoolbox/headtrackedspatialaudio) to place each sound at the center of its intended [`UIScene`](/documentation/UIKit/UIScene) in your multiwindow or multivolume application.

![An illustration of sound spatializing from two windows.](https://docs-assets.developer.apple.com/published/323964a84b824963178ea5b99ae51260/spatializing-sound-from-a-uiscene-01%402x.png)

## [Get the scene’s identifier](/documentation/AudioToolbox/spatializing-sound-from-a-uiscene#Get-the-scenes-identifier)

Placing a sound on a specific [`UIScene`](/documentation/UIKit/UIScene) requires knowledge of the target scene’s [`persistentIdentifier`](/documentation/UIKit/UISceneSession/persistentIdentifier). In a SwiftUI application, that means adding both a [`UIApplicationDelegate`](/documentation/UIKit/UIApplicationDelegate) and [`UISceneDelegate`](/documentation/UIKit/UISceneDelegate) to your SwiftUI App:

```swift

```swift
import SwiftUI 
@main
```swift
```swift
struct MyApplication: App {
```
```
    @UIApplicationDelegateAdaptor var delegate: MyAppDelegate
    var body: some Scene {
        WindowGroup {
            ContentView()
        }
    }
}
```swift
```swift
class MyAppDelegate: NSObject, UIApplicationDelegate, ObservableObject {
```
```
    func application(_ application: UIApplication,
                     configurationForConnecting connectingSceneSession: UISceneSession,
                     options: UIScene.ConnectionOptions) -> UISceneConfiguration {
        let sceneConfig = UISceneConfiguration(name: nil, sessionRole: connectingSceneSession.role)
        sceneConfig.delegateClass = MySceneDelegate.self
        return sceneConfig
    }
}
```swift
```swift
class MySceneDelegate: NSObject, UISceneDelegate, ObservableObject {
```
```
    var sceneIdentifier: String?
    func scene(_ scene: UIScene, willConnectTo session: UISceneSession, options connectionOptions: UIScene.ConnectionOptions) {
        sceneIdentifier = session.persistentIdentifier
    }
}
```

```

The following code makes the identifier for each [`UIScene`](/documentation/UIKit/UIScene) accessible from any SwiftUI [`View`](/documentation/SwiftUI/View) using your [`UISceneDelegate`](/documentation/UIKit/UISceneDelegate) as an [`EnvironmentObject`](/documentation/SwiftUI/EnvironmentObject):

```swift

```swift
import SwiftUI
```swift
```swift
struct ContentView: View {
```
```
    @EnvironmentObject var sceneDelegate: MySceneDelegate
    var body: some View {
        Text("\(String(describing: sceneDelegate.sceneIdentifier))")
    }
}
```

```

## [Anchor the sound to the scene](/documentation/AudioToolbox/spatializing-sound-from-a-uiscene#Anchor-the-sound-to-the-scene)

With a [`UIScene`](/documentation/UIKit/UIScene) identifier in-hand, configure each sound using a [`HeadTrackedSpatialAudio`](/documentation/audiotoolbox/headtrackedspatialaudio) structure.

```swift

```swift
import SwiftUI
import AVFAudio
```swift
```swift
struct ContentView: View {
```
```
    @EnvironmentObject var sceneDelegate: MySceneDelegate
    
    @State var player: AVAudioPlayer? = {
        guard let url = Bundle.main.url(forResource: "my_sound", withExtension: "wav") else {
            return nil
        }
        return try? AVAudioPlayer(contentsOf: url)
    }()
    var body: some View {
        Text("Hello, Sound!")
    }
    .onAppear {
        guard let player = self.player, let sceneID = self.sceneDelegate.sceneIdentifier else {
            return
        }
        
        player.intendedSpatialExperience = .headTracked(.scene(identifier: sceneID))
        player.play()
    }
}
```

```

Besides just [`AVAudioPlayer`](/documentation/AVFAudio/AVAudioPlayer), you can also use [`SpatialAudioExperience`](/documentation/audiotoolbox/spatialaudioexperience) types with the other playback APIs listed below.

## [Spatialize system and alert sounds](/documentation/AudioToolbox/spatializing-sound-from-a-uiscene#Spatialize-system-and-alert-sounds)

Configure the spatial audio experience of your system and alert sounds using:

*   [`AudioServicesPlaySystemSound(_:spatialExperience:)`](/documentation/audiotoolbox/audioservicesplaysystemsound\(_:spatialexperience:\))
    
*   [`AudioServicesPlayAlertSound(_:spatialExperience:)`](/documentation/audiotoolbox/audioservicesplayalertsound\(_:spatialexperience:\))
    

## [Spatialize audio-only playback APIs](/documentation/AudioToolbox/spatializing-sound-from-a-uiscene#Spatialize-audio-only-playback-APIs)

Configure the spatial audio experience of audio-only playback APIs using the [`intendedSpatialExperience`](/documentation/AVFAudio/AVAudioPlayer/intendedSpatialExperience-27klj) property on:

*   [AVAudioPlayer](/documentation/AVFAudio/AVAudioPlayer/intendedSpatialExperience-27klj)
    
*   [AVAudioOutputNode](/documentation/AVFAudio/AVAudioOutputNode/intendedSpatialExperience-3ts59)
    
*   [AUAudioUnit](/documentation/AudioToolbox/AUAudioUnit/intendedSpatialExperience-7uqrm)
    
*   [CHHapticEngine](/documentation/CoreHaptics/CHHapticEngine/intendedSpatialExperience-55ca0)
    

## [Spatialize audio playback APIs that also have video](/documentation/AudioToolbox/spatializing-sound-from-a-uiscene#Spatialize-audio-playback-APIs-that-also-have-video)

Setting a scene identifier on playback APIs that have video content isn’t always necessary as their sound automatically anchors to its visual counterpart. However, if there is no video or if you prefer something besides the automatic behavior, configure the spatial audio experience of these playback APIs using the [`intendedSpatialAudioExperience`](/documentation/AVFoundation/AVPlayer/intendedSpatialAudioExperience-1bd87) property on:

*   [AVPlayer](/documentation/AVFoundation/AVPlayer/intendedSpatialAudioExperience-1bd87)
    
*   [AVSampleBufferRenderSynchronizer](/documentation/AVFoundation/AVSampleBufferRenderSynchronizer/intendedSpatialAudioExperience-3z7d3)
    

## [See Also](/documentation/AudioToolbox/spatializing-sound-from-a-uiscene#see-also)

### [Playback and Recording](/documentation/AudioToolbox/spatializing-sound-from-a-uiscene#Playback-and-Recording)

[

API Reference

Audio Queue Services](/documentation/audiotoolbox/audio-queue-services)

Connect to audio hardware and manage the recording or playback process.

[

API Reference

Audio Services](/documentation/audiotoolbox/audio-services)

Play short sounds or trigger a vibration effect on iOS devices with the appropriate hardware.

[

API Reference

Music Player](/documentation/audiotoolbox/music-player)

Create and play a sequence of tracks, and manage aspects of playback in response to standard events.