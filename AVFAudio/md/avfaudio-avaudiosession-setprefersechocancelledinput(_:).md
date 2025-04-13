

- AVFAudio
- AVAudioSession
-  setPrefersEchoCancelledInput(\_:) 

Instance Method

# setPrefersEchoCancelledInput(\_:)

Sets a preference to enable echo-canceled input on supported hardware.

iOS 18.2+iPadOS 18.2+Mac Catalyst 18.2+

``` source
func setPrefersEchoCancelledInput(_ value: Bool) throws
```

## Parameters 

`value`  

A Boolean value that indicates the preference to set.

## Discussion

Apps may want to record the built-in microphone’s input while also playing audio with the built-in speaker. Enabling echo-canceled input is useful when the app needs the input signal to be clear of any echoes from the audio playing out of the built-in speaker.

Audio sessions using Apple’s voice processing APIs don’t need this option because the system automatically applies echo cancellation to these routes. The voice processing solution is tuned for voice signals, unlike this option, which is tuned for better capture of a wider range of audio signals in the presence of built-in speaker echo.

This option is valid only when used with playAndRecord category and default mode, and is only available on certain 2024 or later iPhone models. Query the isEchoCancelledInputAvailable property to determine whether a device supports this setting. Other recording sessions might be interrupted if this option is not compatible with sessions that are already recording.

After an audio session goes active, you can query the isEchoCancelledInputEnabled property to test whether the system honored the setting.

Note

The input’s enabled state may change if the audio route changes to one that doesn’t support echo cancellation, such as switching to a headset.

## See Also

### Configuring echo cancellation

var isEchoCancelledInputAvailable: Bool

A Boolean value that indicates whether the built-in microphone and speaker route supports echo cancellation.

var isEchoCancelledInputEnabled: Bool

A Boolean value that indicates whether an echo-canceled input is in an enabled state.

var prefersEchoCancelledInput: Bool

A Boolean value that indicates the audio session’s preference for using an echo-canceled input.

