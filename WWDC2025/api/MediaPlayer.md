Framework

# Media Player

Find and play songs, audio podcasts, audio books, and more from within your app.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.1+macOS 10.12.1+tvOS 9.0+visionOS 1.0+watchOS 5.0+

## [Overview](/documentation/MediaPlayer#overview)

Use the Media Player framework, which is part of [MusicKit](https://developer.apple.com/musickit/), to control playback of the user’s media from your app. If your app incorporates music, you can use this framework to search for audio content, such as songs, podcasts, and books, in the user’s library. You can then play that content directly or ask the system Music app to play it. For example, a game might give users the option to play their own music while completing a particular game level.

Important

To protect user privacy, users need to grant permission for your app to access their media library. Add the [`NSAppleMusicUsageDescription`](/documentation/BundleResources/Information-Property-List/NSAppleMusicUsageDescription) key to your app’s `Info.plist` file, and include a description of how you intend to use the user’s library. If this key isn’t present, the system terminates your app when it tries to access the user’s library.

To play content from the user’s library using the Media Player framework, use one of the built-in [`MPMusicPlayerController`](/documentation/mediaplayer/mpmusicplayercontroller) objects:

*   An _application player_ plays music locally within your app. Use this player when you want greater control over the audio you play for the user. This player doesn’t change the state of the built-in Music app.
    
*   The _system player_ employs the Music app to play audio on your behalf. Use this player when you want audio to continue playing even when the user switches away from your app.
    

Use media queries to retrieve the items you want to play and to populate the queue for the media player you select. After a user gives your app permission to access their Apple Music account, it can add songs, create playlists, and play songs from Apple Music. If your app detects that the user isn’t an Apple Music subscriber, it can offer a trial.

You can’t play video media items directly using the Media Player framework. To play videos containing [`MPMediaItem`](/documentation/mediaplayer/mpmediaitem) objects, use an [`AVPlayer`](/documentation/AVFoundation/AVPlayer) object from [AVFoundation](/documentation/AVFoundation). The system player also provides a way to play video items using the system apps.

Important

Only use this framework to facilitate playback of the user’s audio content within your app. Don’t gather information about the user’s audio content for any other purpose. For more information about accessing Apple Music content, see the [App Store review guidelines](https://developer.apple.com/app-store/review/guidelines/#apple-sites-and-services).

## [Topics](/documentation/MediaPlayer#topics)

### [Essentials](/documentation/MediaPlayer#Essentials)

[`NSAppleMusicUsageDescription`](/documentation/BundleResources/Information-Property-List/NSAppleMusicUsageDescription)

A message that tells the user why the app is requesting access to the user’s media library.

### [Built-in music playback](/documentation/MediaPlayer#Built-in-music-playback)

[

Playing audio using the built-in music player](/documentation/mediaplayer/playing-audio-using-the-built-in-music-player)

Create a media player inside your app to play audio from the user’s media library.

```swift
```swift
```swift
class MPMusicPlayerController
```
```

An object that plays audio media items from the device’s Music app library.
```
```swift
```swift
```swift
protocol MPMediaPlayback
```
```

A protocol that defines the interface for controlling audio media playback.
```
```swift
```swift
```swift
protocol MPSystemMusicPlayerController
```
```

A protocol for playing videos in the Music app.
```

### [Media library synchronization](/documentation/MediaPlayer#Media-library-synchronization)

```swift
```swift
```swift
```swift
class MPMediaLibrary
```
```

An object that represents the state of synced media items on a device.
```
```

### [Media item queries](/documentation/MediaPlayer#Media-item-queries)

[

Using filters to create specialized queries](/documentation/mediaplayer/using-filters-to-create-specialized-queries)

Add a filter set to a query before populating a music player queue.

```swift
```swift
```swift
class MPMediaQuery
```
```

A query that specifies a set of media items from the device’s media library using a filter and a grouping type.
```
```swift
```swift
```swift
class MPMediaQuerySection
```
```

A range of media items or media item collections from within a media query.
```
```swift
```swift
```swift
class MPMediaPropertyPredicate
```
```

A set of predicates for defining a filter in a media query.
```
```swift
```swift
```swift
class MPMediaPredicate
```
```

An abstract class that defines classes for filtering media in a media query.
```

### [Media player queues](/documentation/MediaPlayer#Media-player-queues)

```swift
```swift
```swift
```swift
class MPMusicPlayerControllerQueue
```
```

An immutable queue containing the media items to play.
```
```swift
```swift
```swift
class MPMusicPlayerControllerMutableQueue
```
```

A mutable queue containing the media items to play.
```
```swift
```swift
```swift
class MPMusicPlayerApplicationController
```
```

A media player object that you use to revise the queue that’s currently playing.
```
```swift
```swift
```swift
class MPMusicPlayerMediaItemQueueDescriptor
```
```

A set of properties and methods for modifying audio media items in the player’s media queue.
```
```swift
```swift
```swift
class MPMusicPlayerStoreQueueDescriptor
```
```

A set of properties and methods for modifying items, based on their store identifier, in the player’s queue.
```
```swift
```swift
```swift
class MPMusicPlayerPlayParametersQueueDescriptor
```
```

A set of properties and methods for modifying how to play items, based on play parameters the framework returns.
```
```swift
```swift
```swift
class MPMusicPlayerQueueDescriptor
```
```

The abstract base class for audio media item and store queue descriptors.
```
```

### [Media items and playlists](/documentation/MediaPlayer#Media-items-and-playlists)

```swift
```swift
```swift
```swift
class MPMediaItem
```
```

A collection of properties that represents a single item in the media library.
```
```swift
```swift
```swift
class MPMediaItemArtwork
```
```

A graphical image, such as music album cover art, associated with a media item.
```
```swift
```swift
```swift
class MPMediaItemAnimatedArtwork
```
```

An animated image, such as an animated music album cover art, for a media item.

Beta
```
```swift
```swift
```swift
class MPMediaItemCollection
```
```

A sorted set of media items from the media library.
```
```swift
```swift
```swift
class MPMediaPlaylist
```
```

A playable collection of related media items.
```
```swift
```swift
```swift
class MPMediaPlaylistCreationMetadata
```
```

A set of attributes for describing a playlist when creating it.
```
```swift
```swift
```swift
class MPMediaEntity
```
```

The abstract superclass for media items, media item collections, and media playlist instances.
```
```

### [Media player user interface](/documentation/MediaPlayer#Media-player-user-interface)

[

Displaying a media picker from your app](/documentation/mediaplayer/displaying-a-media-picker-from-your-app)

Let users choose the music they want to play by displaying a media picker interface from within your app.

```swift
```swift
```swift
class MPMediaPickerController
```
```

A specialized view controller that provides a graphical interface for selecting media items.
```
```swift
```swift
```swift
class MPVolumeView
```
```

A slider control for setting the system audio output volume, and a button for choosing the audio output route.
```

### [Now Playing information](/documentation/MediaPlayer#Now-Playing-information)

Provide information about the current track.

[

Becoming a now playable app](/documentation/mediaplayer/becoming-a-now-playable-app)

Ensure your app is eligible to become the Now Playing app by adopting best practices for providing Now Playing info and registering for remote command center actions.

```swift
```swift
```swift
class MPNowPlayingSession
```
```

An object that manages Now Playing information and remote commands for multiple players.
```
```swift
```swift
```swift
class MPNowPlayingInfoCenter
```
```

An object for setting the Now Playing information for media that your app plays.
```
```swift
```swift
```swift
class MPNowPlayingInfoLanguageOption
```
```

A set of interfaces for setting the language option for the Now Playing item.
```
```swift
```swift
```swift
class MPNowPlayingInfoLanguageOptionGroup
```
```

A grouped set of language options where only a single language option can be active at a time.
```

[

API Reference

Language option characteristic constants](/documentation/mediaplayer/language-option-characteristic-constants)

The constants for defining language characteristics.

### [External player and system event handling](/documentation/MediaPlayer#External-player-and-system-event-handling)

Support playback controls on external media players or system-provided controls.

[

Handling external player events notifications](/documentation/mediaplayer/handling-external-player-events-notifications)

Handle events for external media players.

[

API Reference

Remote command center events](/documentation/mediaplayer/remote-command-center-events)

Set up the remote command center to handle media player events.

[

API Reference

Track navigation events](/documentation/mediaplayer/track-navigation-events)

Respond to requests to change which part of a media item plays.

[

API Reference

Media playback mode events](/documentation/mediaplayer/media-playback-mode-events)

Respond to changes in the way media items play.

[

API Reference

Feedback and rating events](/documentation/mediaplayer/feedback-and-rating-events)

Respond to incoming feedback and rating events.

### [External media player items](/documentation/MediaPlayer#External-media-player-items)

Provide content and interact with external media players.

```swift
```swift
```swift
class MPContentItem
```
```

An object that contains the information for a displayed media item.
```

### [Media player errors](/documentation/MediaPlayer#Media-player-errors)

```swift
```swift
```swift
```swift
struct MPError
```
```

A structure that represents a framework error.
```
```swift
```swift
```swift
enum Code
```
```

An enumeration that represents error codes for framework operations.
```
```swift
```swift
```swift
let MPErrorDomain: String
```
```

The Media Player framework error domain.
```
```

### [Deprecated](/documentation/MediaPlayer#Deprecated)

[

API Reference

Deprecated types](/documentation/mediaplayer/deprecated-types)

Review deprecated symbols and avoid using them in your app.