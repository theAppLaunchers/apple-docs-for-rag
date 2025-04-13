

- Media Player
- MPNowPlayingInfoCenter
-  default() 

Type Method

# default()

Returns the singleton Now Playing info center.

iOS 5.0+iPadOS 5.0+Mac Catalyst 13.1+macOS 10.12.2+tvOS 5.0+visionOS 1.0+watchOS 5.0+

``` source
class func `default`() -> MPNowPlayingInfoCenter
```

## Return Value

The now playing info center singleton.

## Discussion

The default now playing info center holds Now Playing information for the app that’s designated to receive remote control events. For information on how to configure your app to receive remote control events, see Handling external player events notifications.

## See Also

### Working with the default Now Playing info center

var nowPlayingInfo: [String : Any]?

The current Now Playing information for the default Now Playing info center.

enum MPNowPlayingInfoMediaType

The type of media currently playing.

