

- AVFAudio
- AVAudioSession
- AVAudioSession.CategoryOptions
-  allowBluetoothA2DP 

Type Property

# allowBluetoothA2DP

An option that determines whether you can stream audio from this session to Bluetooth devices that support the Advanced Audio Distribution Profile (A2DP).

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+tvOS 10.0+visionOS 1.0+watchOS 3.0+

``` source
static var allowBluetoothA2DP: AVAudioSession.CategoryOptions { get }
```

## Discussion

A2DP is a stereo, output-only profile intended for higher bandwidth audio use cases, such as music playback. The system automatically routes to A2DP ports if you configure an app’s audio session to use the ambient, soloAmbient, or playback categories.

Starting with iOS 10.0, apps using the playAndRecord category may also allow routing output to paired Bluetooth A2DP devices. To enable this behavior, pass this category option when setting your audio session’s category.

Audio sessions using the multiRoute or record categories implicitly clear this option. If you clear it, paired Bluetooth A2DP devices don’t show up as available audio output routes.

Note

If this option and the allowBluetooth option are both set, when a single device supports both the Hands-Free Profile (HFP) and A2DP, the system gives hands-free ports a higher priority for routing.

## See Also

### Getting Standard Session Options

static var mixWithOthers: AVAudioSession.CategoryOptions

An option that indicates whether audio from this session mixes with audio from active sessions in other audio apps.

static var duckOthers: AVAudioSession.CategoryOptions

An option that reduces the volume of other audio sessions while audio from this session plays.

static var interruptSpokenAudioAndMixWithOthers: AVAudioSession.CategoryOptions

An option that determines whether to pause spoken audio content from other sessions when your app plays its audio.

static var allowBluetooth: AVAudioSession.CategoryOptions

An option that determines whether Bluetooth hands-free devices appear as available input routes.

static var allowAirPlay: AVAudioSession.CategoryOptions

An option that determines whether you can stream audio from this session to AirPlay devices.

static var defaultToSpeaker: AVAudioSession.CategoryOptions

An option that determines whether audio from the session defaults to the built-in speaker instead of the receiver.

static var overrideMutedMicrophoneInterruption: AVAudioSession.CategoryOptions

An option that indicates whether the system interrupts the audio session when it mutes the built-in microphone.

