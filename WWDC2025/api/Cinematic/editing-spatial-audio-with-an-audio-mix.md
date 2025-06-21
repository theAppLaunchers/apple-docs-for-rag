*   [Cinematic](/documentation/cinematic)
*   Editing Spatial Audio with an audio mix Beta

Sample Code

# Editing Spatial Audio with an audio mix

Add Spatial Audio editing capabilities with the Audio Mix API in the Cinematic framework.

[Download](https://docs-assets.developer.apple.com/published/031e7e4af49c/EditingSpatialAudioWithAnAudioMix.zip)

macOS 26.0+BetaXcode 26.0+Beta

## [Overview](/documentation/Cinematic/editing-spatial-audio-with-an-audio-mix#Overview)

Beginning with iPhone 16, you can use Spatial Audio capture to record video with 3D audio, and edit the audio mix in the Photos app. With Audio Mix, you have creative control of the background and foreground sounds in a recording. It isolates speech as foreground and ambience as background, and you can select between multiple creative rendering styles to adjust the mix.

The `SpatialAudioCLI` sample project is a command-line tool that demonstrates three different methods for applying an audio mix: using [`AVPlayer`](/documentation/AVFoundation/AVPlayer), using [`AVAssetWriter`](/documentation/AVFoundation/AVAssetWriter), and using [`AUAudioMix`](/documentation/AudioToolbox/kAudioUnitSubType_AUAudioMix).

Note

This sample code project is associated with WWDC25 session 251: [Enhance your app’s audio content creation capabilities](https://developer.apple.com/videos/play/wwdc2025/251).

### [Configure the sample code project](/documentation/Cinematic/editing-spatial-audio-with-an-audio-mix#Configure-the-sample-code-project)

For best results, use `SpatialAudioCLI` with media that contains a Spatial Audio track. On all iPhone 16 models, Spatial Audio recording is available when capturing video with the Camera app. See the [iPhone User Guide](https://support.apple.com/en-kw/guide/iphone/iph31c1ca6c7/ios) for how to change sound recording options.

You can record Spatial Audio in your app by setting the [`multichannelAudioMode`](/documentation/AVFoundation/AVCaptureDeviceInput/multichannelAudioMode) property of the [`AVCaptureDeviceInput`](/documentation/AVFoundation/AVCaptureDeviceInput) to a value of `firstOrderAmbisonics`.

### [Adjust the audio mix in AVPlayer](/documentation/Cinematic/editing-spatial-audio-with-an-audio-mix#Adjust-the-audio-mix-in-AVPlayer)

The simplest way to adjust the audio mix is to play Spatial Audio assets with [`AVPlayer`](/documentation/AVFoundation/AVPlayer).

First, the sample loads the specified input file into an [`AVPlayerItem`](/documentation/AVFoundation/AVPlayerItem):

```swift
```swift
```swift
```swift
```swift
```swift
let myAsset = AVURLAsset(url: URL(filePath: "myMediaURL"))
```
```
```swift
```swift
let myPlayerItem = AVPlayerItem(asset: myAsset)
```
```
```
```
```
```

Then the sample uses the [`AVAsset`](/documentation/AVFoundation/AVAsset) to initialize an instance of `CNAssetSpatialAudioInfo`:

```swift

```swift
do {
    // This command throws if the input file does not have proper Spatial Audio.
    let audioInfo = try await CNAssetSpatialAudioInfo(asset: myAsset)
} catch {
    print("A problem occured reading the spatial audio asset: \(error)")
}
```

```

The two primary mix parameters are `effectIntensity` and `renderingStyle`. The sample creates an [`AVAudioMix`](/documentation/AVFoundation/AVAudioMix) with the specified mix parameters and sets it on the [`AVPlayerItem`](/documentation/AVFoundation/AVPlayerItem):

```swift

```swift
// Sets the mix parameters.
```swift
```swift
let intensity = 0.5 // Float values between 0.0 and 1.0.
```
```
```swift
```swift
let style = CNSpatialAudioRenderingStyle.cinematic
```
```
// Creates an `AVAudioMix` with effect intensity and rendering style.   
```swift
```swift
let newAudioMix = audioInfo.audioMix(effectIntensity: intensity, renderingStyle: style)
```
```
myPlayerItem.audioMix = newAudioMix
// AVPlayer plays the asset with the new audio mix parameters.
```swift
```swift
let player = AVPlayer(playerItem: myPlayerItem)
```
```
```

```

## [See Also](/documentation/Cinematic/editing-spatial-audio-with-an-audio-mix#see-also)

### [Editing](/documentation/Cinematic/editing-spatial-audio-with-an-audio-mix#Editing)

```swift
```swift
```swift
```swift
struct CNDetection
```
```

A structure that represents a detected subject, face, torso or pet at a particular time.
```
```swift
```swift
```swift
struct CNDecision
```
```

An object that represents a decision to focus on a particular detection, or group of detections, at a particular time.
```
```swift
```swift
```swift
class CNDetectionTrack
```
```

An object representing a series of detections of the same subject over time.
```
```swift
```swift
```swift
class CNFixedDetectionTrack
```
```

An object representing the fixed detection track.
```
```swift
```swift
```swift
class CNCustomDetectionTrack
```
```

An object representing a discrete detection track composed of individual detections.
```
```swift
```swift
```swift
enum CNDetectionType
```
```

The type of object detected, such as face, torso, cat, dog and so on.
```
```

Beta Software

This documentation contains preliminary information about an API or technology in development. This information is subject to change, and software implemented according to this documentation should be tested with final operating system software.

[Learn more about using Apple's beta software](https://developer.apple.com/support/beta-software/)