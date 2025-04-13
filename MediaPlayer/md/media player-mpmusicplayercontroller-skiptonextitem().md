

- Media Player
- MPMusicPlayerController
-  skipToNextItem() 

Instance Method

# skipToNextItem()

Starts playback of the next media item in the playback queue, or if the music player isn’t playing, designates the next media item as the next item to play.

iOS 3.0+iPadOS 3.0+Mac Catalyst 13.1+tvOS 14.0+visionOS 1.0+

``` source
func skipToNextItem()
```

## Discussion

Calling this method when already at the last item in the playback queue ends playback.

## See Also

### Related Documentation

var nowPlayingItem: MPMediaItem?

The currently-playing media item, or the media item in a queue that you designated to begin playback with.

### Controlling playback

func skipToBeginning()

Restarts playback at the beginning of the currently playing media item.

func skipToPreviousItem()

Starts playback of the previous media item in the playback queue, or if the music player isn’t playing, designates the previous media item as the next to play.

func append(MPMusicPlayerQueueDescriptor)

Inserts the media items defined by the queue descriptor after the last media item in the current queue.

func prepend(MPMusicPlayerQueueDescriptor)

Inserts the media items defined by the queue descriptor into the current queue immediately after the currently playing media item.

