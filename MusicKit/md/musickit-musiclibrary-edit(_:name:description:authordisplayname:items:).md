

- MusicKit
- MusicLibrary
-  edit(\_:name:description:authorDisplayName:items:) 

Instance Method

# edit(\_:name:description:authorDisplayName:items:)

Edits a playlist that your app has created including items to rebuild the list of entries.

iOS 16.0+iPadOS 16.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
@discardableResult
func edit(
    _ playlist: Playlist,
    name: String? = nil,
    description: String? = nil,
    authorDisplayName: String? = nil,
    items: S
) async throws -> Playlist where S : Sequence, MusicPlaylistAddableType : MusicPlaylistAddable, MusicPlaylistAddableType == S.Element
```

## Return Value

The edited playlist.

## Discussion

This function will throw an error if your app attempts to edit a playlist that another app created.

