

- WatchKit
- WKInterfaceController
-  presentMediaPlayerController(with:options:completion:) 

Instance Method

# presentMediaPlayerController(with:options:completion:)

Displays a modal interface for playing the specified media file.

watchOS 2.0+

``` source
@MainActor
func presentMediaPlayerController(
    with URL: URL,
    options: [AnyHashable : Any]? = nil,
    completion: @escaping (Bool, TimeInterval, (any Error)?) -> Void
)
```

``` source
@MainActor
func presentMediaPlayerController(
    with URL: URL,
    options: [AnyHashable : Any]? = nil
) async throws -> (Bool, TimeInterval)
```

## Parameters 

`URL`  

The URL of the media file you want to play. The URL must specify a file; streamed media is not supported. The file may contain audio, video, or both.

If you specify a URL for a file on a remote server, this method downloads the file first and displays a progress indicator showing the progress of the operation. Because WatchKit uses App Transport Security (ATS) when downloading files from a web server, the file must be on a secure server, and the URL must use the `https` scheme. If your server does not support ATS–level security, download the file yourself before playing it.

`options`  

An optional dictionary of playback options for the media file. For a list of keys to include in the dictionary, see Media Player Options.

`completion`  

The block to execute when playback ends. Use this block to determine the status of playback and to perform any cleanup. This block has no return value and takes the following parameters:

didPlayToEnd  
A Boolean value indicating whether the media file finished playing. The value is true if the end of the media file was reached or false if playback ended prematurely.

endTime  
The time (in seconds) at which playback ended. When the `didPlayToEnd` parameter is false, you can use the value in this property to determine when playback stopped. You might use that value as the start time if you play the content again.

error  
An error object if a problem occurred. Use the error object to determine the cause of the problem and take any appropriate actions, such as notifying the user.

## Mentioned in 

Navigating Between Scenes

## Discussion

Use this method to present short media clips to the user. This method executes asynchronously, returning shortly after you call it. During a subsequent run loop cycle, the system presents a media interface controller over the current interface controller. For video, the interface controller displays the video content along with controls to start and stop playback. For audio, the interface controller displays information about the content being played. Always call this method from your WatchKit extension’s main thread.

When the user dismisses the interface, or when you dismiss the media player programmatically, WatchKit calls the block provided in the `completion` parameter. Use that block to find out how much of the media file was played or other relevant information. For example, you might note the stopping point and start playback of the same clip from that point later.

The following table lists the encoding information to use when creating media files. For audio and video assets played directly from your app, keep your clips relatively short. Short clips consume less space on disk, use less power, and take less time to download.

| Media type | Recommended encoding |
|----|----|
| Video assets | Video codec: H.264 High Profile  Bit rate: 160 kpbs at up to 30 fps  Full screen resolution: 208 x 260 in portrait orientation  16:9 resolution: 320 x 180 in landscape orientation  Audio bit rate: 32 kpbs stereo |
| Audio-only assets | Bit rate: 32 kbps stereo |

Note

Do not attempt to play audio or video content while gathering heart rate data using Health Kit. If you present a media interface, WatchKit automatically disables the gathering of heart rate data.

Any audio you play using this method is routed to a paired Bluetooth audio device if one is available. If no Bluetooth audio device is available, audio is routed to to the Apple Watch speaker.

## See Also

### Presenting video and audio interfaces

Media Player Options

Keys indicating media playback options.

func dismissMediaPlayerController()

Dismisses the media interface controller.

func presentAudioRecorderController(withOutputURL: URL, preset: WKAudioRecorderPreset, options: [AnyHashable : Any]?, completion: (Bool, (any Error)?) -> Void)

Display a standard interface for recording audio from the user’s Apple Watch.

enum WKAudioRecorderPreset

Constants indicating the quality of audio recordings.

Audio Recording Options

Options to specify when recording audio.

func dismissAudioRecorderController()

Dismisses the audio recording interface controller.

