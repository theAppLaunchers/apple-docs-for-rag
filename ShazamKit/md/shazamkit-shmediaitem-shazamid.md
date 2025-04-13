

- ShazamKit
- SHMediaItem
-  shazamID 

Instance Property

# shazamID

The Shazam ID for the song.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
var shazamID: String? { get }
```

## See Also

### Working with Shazam music catalog media items

var webURL: URL?

A link to the Shazam Music catalog page that contains the full information for the song.

class func fetch(shazamID: String, completionHandler: (SHMediaItem?, (any Error)?) -> Void)

Requests the media item for the song with the specified Shazam ID.

