

- Media Player
- MPRemoteCommandCenter
-  changeShuffleModeCommand 

Instance Property

# changeShuffleModeCommand

The command object for changing the shuffle mode.

iOS 7.1+iPadOS 7.1+Mac Catalyst 13.1+macOS 10.12.2+tvOS 7.1+visionOS 1.0+watchOS 5.0+

``` source
var changeShuffleModeCommand: MPChangeShuffleModeCommand { get }
```

## Discussion

Use the object in this property to register your app’s handler for changing the shuffle mode for the playlist. In your handler, change the shuffle mode to the new value. You can disable the command if your app does not support it.

## See Also

### Navigating between tracks

var nextTrackCommand: MPRemoteCommand

The command object for selecting the next track.

var previousTrackCommand: MPRemoteCommand

The command object for selecting the previous track.

var changeRepeatModeCommand: MPChangeRepeatModeCommand

The command object for changing the repeat mode.

