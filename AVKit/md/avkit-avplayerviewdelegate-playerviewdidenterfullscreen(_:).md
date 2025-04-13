

- AVKit
- AVPlayerViewDelegate
-  playerViewDidEnterFullScreen(\_:) 

Instance Method

# playerViewDidEnterFullScreen(\_:)

Tells the delegate that the player view entered full-screen mode.

macOS 12.0+

``` source
optional func playerViewDidEnterFullScreen(_ playerView: AVPlayerView)
```

## Parameters 

`playerView`  

The player view.

## See Also

### Responding to Full Screen Events

func playerViewWillEnterFullScreen(AVPlayerView)

Tells the delegate that the player view is about to enter full-screen mode.

func playerViewWillExitFullScreen(AVPlayerView)

Tells the delegate that the player view is about to exit full-screen mode.

func playerViewDidExitFullScreen(AVPlayerView)

Tells the delegate that the player view exited full-screen mode.

func playerView(AVPlayerView, restoreUserInterfaceForFullScreenExitWithCompletionHandler: (Bool) -> Void)

Tells the delegate to restore the app’s user interface when exiting full-screen mode.

