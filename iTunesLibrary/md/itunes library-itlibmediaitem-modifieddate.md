

- iTunes Library
- ITLibMediaItem
-  modifiedDate 

Instance Property

# modifiedDate

The date and time that iTunes last modified the media item.

Mac Catalyst 14.0+macOS 10.13+

``` source
var modifiedDate: Date? { get }
```

## See Also

### Getting Media Item Info

var title: String

The title of the media item.

var sortTitle: String?

The title of the media item to use when sorting.

var artist: ITLibArtist?

Information about the artist that iTunes associates with the media item.

var composer: String

The name of the composer that iTunes associates with the media item.

var sortComposer: String?

The name to use when sorting by composer.

var rating: Int

The rating of the media item.

var isRatingComputed: Bool

A Boolean value that indicates whether iTunes computes the media item’s rating from its album rating.

var startTime: Int

If nonzero, the actual time playback of the media item starts instead of 0:00 (in milliseconds).

var stopTime: Int

If nonzero, the actual time playback of the media item stops versus the total time (in milliseconds).

var album: ITLibAlbum

The album of the media item.

var genre: String

The genre of the media item, if any.

var kind: String?

The kind of media item file, such as an MPEG audio file.

var mediaKind: ITLibMediaItemMediaKind

The kind of media item.

var totalTime: Int

The length of the media item in milliseconds.

var trackNumber: Int

The position of the media item within its album.

