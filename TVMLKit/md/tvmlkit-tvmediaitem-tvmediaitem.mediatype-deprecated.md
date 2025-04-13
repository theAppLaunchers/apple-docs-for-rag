

- TVMLKit
- TVMediaItem
-  TVMediaItem.MediaType Deprecated

Structure

# TVMediaItem.MediaType

A value indicating whether the media is audio or video.

tvOS 12.0–18.0Deprecated

``` source
struct MediaType
```

Deprecated

Please use SwiftUI or UIKit

## Topics

### Media Types

static let audio: TVMediaItem.MediaType

The media item is audio only.

static let video: TVMediaItem.MediaType

The media item incorporates video.

### Initializers

init(String)

init(rawValue: String)

## Relationships

### Conforms To

- Equatable
- Hashable
- RawRepresentable
- Sendable

## See Also

### Identifying Media Items

var artworkImageURL: URL?

The URL path to the artwork that accompanies the media item.

Deprecated

var itemDescription: String?

The description for a media item.

Deprecated

var subtitle: String?

The subtitle for a media item.

Deprecated

var title: String?

The title for a media item.

Deprecated

var type: TVMediaItem.MediaType?

The type of media item.

Deprecated

var url: URL?

The URL path to the media item.

Deprecated

var userInfo: [String : Any]

User-defined metadata, like a developer-specific identifier, for a media item.

Deprecated

