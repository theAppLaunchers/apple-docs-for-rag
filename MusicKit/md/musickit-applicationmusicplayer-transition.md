

- MusicKit
- ApplicationMusicPlayer
-  transition 

Instance Property

# transition

The transition between items for the application music player.

iOS 18.0+iPadOS 18.0+

``` source
var transition: MusicPlayer.Transition { get set }
```

## Discussion

By default, the `transition` is `.none` where there is no transition between playing items.

Your application should set the desired transition before setting the queue.

The player cannot apply transitions in all scenarios. For example, the player does not apply a transition between two consecutive tracks in an album.

