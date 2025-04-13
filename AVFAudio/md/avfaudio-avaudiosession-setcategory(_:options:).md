

- AVFAudio
- AVAudioSession
-  setCategory(\_:options:) 

Instance Method

# setCategory(\_:options:)

Sets the audio session’s category with the specified options.

iOS 6.0+iPadOS 6.0+Mac Catalyst 13.1+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func setCategory(
    _ category: AVAudioSession.Category,
    options: AVAudioSession.CategoryOptions = []
) throws
```

## Parameters 

`category`  

The category to apply to the audio session. See AVAudioSession.Category for supported category values.

`options`  

A mask of additional options for handling audio. For a list of constants, see AVAudioSession.CategoryOptions.

## Discussion

The audio session’s category defines how you intend to use audio in your app. Typically, you set the category before activating the session. You can also set the category while the session is active, but doing so results in an immediate route change.

You can tailor the behavior of certain categories by specifying a mask of category options. Specifying an unsupported option for the indicated category results in an error. See AVAudioSession.CategoryOptions for category compatibility.

Note

Instead of setting your category and mode properties independently, set them at the same time using the setCategory(_:mode:options:) or setCategory(_:mode:policy:options:) method.

## See Also

### Configuring standard audio behaviors

func setCategory(AVAudioSession.Category, mode: AVAudioSession.Mode, policy: AVAudioSession.RouteSharingPolicy, options: AVAudioSession.CategoryOptions) throws

Sets the session category, mode, route-sharing policy, and options.

func setCategory(AVAudioSession.Category, mode: AVAudioSession.Mode, options: AVAudioSession.CategoryOptions) throws

Sets the audio session’s category, mode, and options.

func setCategory(AVAudioSession.Category) throws

Sets the audio session’s category.

func setMode(AVAudioSession.Mode) throws

Sets the audio session’s mode.

