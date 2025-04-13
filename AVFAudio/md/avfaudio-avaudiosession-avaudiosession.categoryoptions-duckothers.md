

- AVFAudio
- AVAudioSession
- AVAudioSession.CategoryOptions
-  duckOthers 

Type Property

# duckOthers

An option that reduces the volume of other audio sessions while audio from this session plays.

iOSiPadOSMac CatalysttvOSvisionOSwatchOS

``` source
static var duckOthers: AVAudioSession.CategoryOptions { get }
```

## Discussion

You can set this option only if the audio session category is playAndRecord, playback, or multiRoute. Setting it implicitly sets the mixWithOthers option.

Use this option to mix your app’s audio with that of others. While your app plays audio, the system reduces the volume of other audio sessions to make yours more prominent. If your app provides occasional spoken audio, such as in a turn-by-turn navigation app or an exercise app, you should also set the interruptSpokenAudioAndMixWithOthers option.

Ducking begins when you activate your app’s audio session and ends when you deactivate the session. If you clear this option, activating your session interrupts other audio sessions.

Important

Set this option on a temporary basis only. Don’t use it to duck the audio of other apps for more than a few seconds.

## See Also

### Getting Standard Session Options

static var mixWithOthers: AVAudioSession.CategoryOptions

An option that indicates whether audio from this session mixes with audio from active sessions in other audio apps.

static var interruptSpokenAudioAndMixWithOthers: AVAudioSession.CategoryOptions

An option that determines whether to pause spoken audio content from other sessions when your app plays its audio.

static var allowBluetooth: AVAudioSession.CategoryOptions

An option that determines whether Bluetooth hands-free devices appear as available input routes.

static var allowBluetoothA2DP: AVAudioSession.CategoryOptions

An option that determines whether you can stream audio from this session to Bluetooth devices that support the Advanced Audio Distribution Profile (A2DP).

static var allowAirPlay: AVAudioSession.CategoryOptions

An option that determines whether you can stream audio from this session to AirPlay devices.

static var defaultToSpeaker: AVAudioSession.CategoryOptions

An option that determines whether audio from the session defaults to the built-in speaker instead of the receiver.

static var overrideMutedMicrophoneInterruption: AVAudioSession.CategoryOptions

An option that indicates whether the system interrupts the audio session when it mutes the built-in microphone.

