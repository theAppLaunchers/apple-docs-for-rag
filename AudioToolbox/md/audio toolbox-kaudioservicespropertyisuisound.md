

- Audio Toolbox
-  kAudioServicesPropertyIsUISound 

Global Variable

# kAudioServicesPropertyIsUISound

A `UInt32` value, where `1` means that, for the audio file specified by a system sound passed in the `inSpecifier` parameter, the System Sound server respects the user setting in the Sound Effects preference and is silent when the user turns off sound effects.

iOSiPadOSMac CatalystmacOStvOSvisionOS

``` source
var kAudioServicesPropertyIsUISound: AudioServicesPropertyID { get }
```

## Discussion

This property is set to `1` by default. Set it to `0` for the system sound to always play when passed to AudioServicesPlaySystemSound(_:), regardless of the user’s setting in sound preferences.

## See Also

### Constants

var kAudioServicesPropertyCompletePlaybackIfAppDies: AudioServicesPropertyID

A `UInt32` value, where `1` means that the audio file specified by a system sound passed in the `inSpecifier` parameter should finish playing even if the client application terminates. This could happen, for example, if the user quits or the application terminates unexpectedly while the sound is playing. The default is `0`. That is, you must explicitly set this property’s value to `1` if you want the sound to complete playing even if the application terminates.

