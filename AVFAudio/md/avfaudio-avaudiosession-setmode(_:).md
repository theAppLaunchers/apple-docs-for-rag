

- AVFAudio
- AVAudioSession
-  setMode(\_:) 

Instance Method

# setMode(\_:)

Sets the audio session’s mode.

iOS 5.0+iPadOS 5.0+Mac Catalyst 13.1+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func setMode(_ mode: AVAudioSession.Mode) throws
```

## Parameters 

`mode`  

The audio session mode to apply to the audio session. See AVAudioSession.Mode for supported mode values.

## Discussion

The audio session’s category and mode together define how your app uses audio. Typically, you set the category and mode before activating the session. You can also set the category or mode while the session is active, but doing so results in an immediate change.

Note

Instead of setting your category and mode properties independently, set them at the same time using the setCategory(_:mode:options:) or setCategory(_:mode:policy:options:) method.

## See Also

### Configuring standard audio behaviors

func setCategory(AVAudioSession.Category, mode: AVAudioSession.Mode, policy: AVAudioSession.RouteSharingPolicy, options: AVAudioSession.CategoryOptions) throws

Sets the session category, mode, route-sharing policy, and options.

func setCategory(AVAudioSession.Category, mode: AVAudioSession.Mode, options: AVAudioSession.CategoryOptions) throws

Sets the audio session’s category, mode, and options.

func setCategory(AVAudioSession.Category, options: AVAudioSession.CategoryOptions) throws

Sets the audio session’s category with the specified options.

func setCategory(AVAudioSession.Category) throws

Sets the audio session’s category.

