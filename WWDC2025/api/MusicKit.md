Framework

# MusicKit

Integrate your app with Apple Music.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

## [Overview](/documentation/MusicKit#Overview)

Use MusicKit to integrate your app with [Apple Music API](/documentation/AppleMusicAPI), a web service you use to access information about music items in the Apple Music catalog. Using MusicKit, you can more easily build apps that tie into Apple Music.

The framework provides a model layer for accessing music items in Swift, as well as playback support so you can add music to your app. Additionally, it provides some related user interface elements, such as a view to display images that correspond to artwork for a music item, or a way to present music subscription offers to users who may not have an active Apple Music subscription.

Important

Users must grant permission for your app to access their music data. Add the [NSAppleMusicUsageDescription](/documentation/BundleResources/Information-Property-List/NSAppleMusicUsageDescription) key to your app’s `Info.plist` file, and include a description of how you intend to use the user’s media. If this key isn’t present, the system terminates your app when it tries to access the user’s music.

Request permission for your app to use MusicKit with [`MusicAuthorization`](/documentation/musickit/musicauthorization). Check specific capabilities for the current [`MusicSubscription`](/documentation/musickit/musicsubscription) to ensure your music-related functionality is available to the user. Find music items using a search term with [`MusicCatalogSearchRequest`](/documentation/musickit/musiccatalogsearchrequest), or find music items using a filter with [`MusicCatalogResourceRequest`](/documentation/musickit/musiccatalogresourcerequest). Play music in your app with one of the two music players that MusicKit offers. Allow the user to begin a free trial for Apple Music from within your app by presenting a music subscription offer.

You can load content from an arbitrary Apple Music API endpoint with [`MusicDataRequest`](/documentation/musickit/musicdatarequest) to take further advantage of additional functionality available in Apple Music API.

## [Topics](/documentation/MusicKit#topics)

### [Essentials](/documentation/MusicKit#Essentials)

[

Using Automatic Developer Token Generation for Apple Music API](/documentation/musickit/using-automatic-token-generation-for-apple-music-api)

Enable your app’s integration with the MusicKit App Service in the developer portal.

[

Using MusicKit to Integrate with Apple Music](/documentation/musickit/using_musickit_to_integrate_with_apple_music)

Find an album in Apple Music that corresponds to a CD in a user’s collection, and present the information for the album.

[`NSAppleMusicUsageDescription`](/documentation/BundleResources/Information-Property-List/NSAppleMusicUsageDescription)

A message that tells the user why the app is requesting access to the user’s media library.

### [Music Items](/documentation/MusicKit#Music-Items)

A set of value types represents each kind of music item.

```swift
```swift
```swift
struct Album
```
```

A music item that represents an album.
```
```swift
```swift
```swift
struct Artist
```
```

A music item that represents an artist.
```
```swift
```swift
```swift
struct Curator
```
```

A music item that represents a curator.
```
```swift
```swift
```swift
struct Genre
```
```

A music item that represents a genre.
```
```swift
```swift
```swift
struct MusicVideo
```
```

A music item that represents a music video.
```
```swift
```swift
```swift
struct Playlist
```
```

A music item that represents a playlist.
```
```swift
```swift
```swift
struct RadioShow
```
```

A music item that represents a radio show.
```
```swift
```swift
```swift
struct RecordLabel
```
```

A music item that represents a record label.
```
```swift
```swift
```swift
struct Song
```
```

A music item that represents a song.
```
```swift
```swift
```swift
struct Station
```
```

A music item that represents a station.
```
```swift
```swift
```swift
enum Track
```
```

A music item that represents a track.
```

### [Music Item Attributes](/documentation/MusicKit#Music-Item-Attributes)

A set of structured attributes for music items.

```swift
```swift
```swift
enum ContentRating
```
```

The rating of the content that potentially plays while playing a resource.
```
```swift
```swift
```swift
struct EditorialNotes
```
```

An object that represents editorial notes.
```
```swift
```swift
```swift
struct PreviewAsset
```
```

An object that represents a preview for resources.
```

### [Catalog Search](/documentation/MusicKit#Catalog-Search)

The catalog search request allows your app to find music items in the Apple Music catalog.

```swift
```swift
```swift
struct MusicCatalogSearchRequest
```
```

A request that your app uses to fetch items from the Apple Music catalog using a search term.
```
```swift
```swift
```swift
struct MusicCatalogSearchResponse
```
```

An object that contains results for a catalog search request.
```
```swift
```swift
```swift
protocol MusicCatalogSearchable
```
```

A protocol for music items that your app can fetch by using a catalog search request.
```

### [Resource Loading Using Filters](/documentation/MusicKit#Resource-Loading-Using-Filters)

The catalog resource request allows your app to load items using a specific filter. Each music item type has its own set of properties you can use as a filter for a catalog resource request when loading music items for your app.

```swift
```swift
```swift
struct MusicCatalogResourceRequest
```
```

A request that your app uses to fetch items from the Apple Music catalog using a filter.
```
```swift
```swift
```swift
struct MusicCatalogResourceResponse
```
```

An object that contains results for a catalog resource request.
```
```swift
```swift
```swift
protocol AlbumFilter
```
```

Album properties your app uses as a filter for a catalog resource request.
```
```swift
```swift
```swift
protocol ArtistFilter
```
```

Artist properties your app uses as a filter for a catalog resource request.
```
```swift
```swift
```swift
protocol CuratorFilter
```
```

Curator properties your app uses as a filter for a catalog resource request.
```
```swift
```swift
```swift
protocol GenreFilter
```
```

Genre properties your app uses as a filter for a catalog resource request.
```
```swift
```swift
```swift
protocol MusicVideoFilter
```
```

Music video properties your app uses as a filter for a catalog resource request.
```
```swift
```swift
```swift
protocol PlaylistFilter
```
```

Playlist properties your app uses as a filter for a catalog resource request.
```
```swift
```swift
```swift
protocol RadioShowFilter
```
```

Radio Show properties your app uses as a filter for a catalog resource request.
```
```swift
```swift
```swift
protocol RecordLabelFilter
```
```

The set of record label properties your app uses as a filter for a catalog resource request.
```
```swift
```swift
```swift
protocol SongFilter
```
```

Song properties your app uses as a filter for a catalog resource request.
```
```swift
```swift
```swift
protocol StationFilter
```
```

The set of station properties your app uses as a filter for a catalog resource request.
```
```swift
```swift
```swift
protocol FilterableMusicItem
```
```

A declaration of the associated type that contains the set of music item properties your app uses as a filter for a catalog resource request.
```

### [General Purpose Data Request](/documentation/MusicKit#General-Purpose-Data-Request)

```swift
```swift
```swift
```swift
struct MusicDataRequest
```
```

A request for loading data from an arbitrary Apple Music API endpoint.
```
```swift
```swift
```swift
struct MusicDataResponse
```
```

An object containing results for a data request.
```
```

### [Playback](/documentation/MusicKit#Playback)

```swift
```swift
```swift
```swift
class ApplicationMusicPlayer
```
```

An object your app uses to play music in a way that doesn’t affect the Music app’s state.
```
```swift
```swift
```swift
class SystemMusicPlayer
```
```

An object your app uses to play music by controlling the Music app’s state.
```
```swift
```swift
```swift
class MusicPlayer
```
```

An object your app uses to play music.
```
```swift
```swift
```swift
protocol PlayableMusicItem
```
```

A set of properties that a music player uses to initiate playback for a music item.
```
```swift
```swift
```swift
struct PlayParameters
```
```

An opaque object that represents parameters to initiate playback of a playable music item using a music player.
```
```

### [Artwork](/documentation/MusicKit#Artwork)

```swift
```swift
```swift
```swift
struct Artwork
```
```

An object that represents artwork for a music item.
```
```swift
```swift
```swift
struct ArtworkImage
```
```

A view that displays the image for a music item’s artwork.
```
```

### [Authorization](/documentation/MusicKit#Authorization)

Before you can use any of the functionality of the framework, you need to request the user’s informed consent for your app to access their music data.

```swift
```swift
```swift
struct MusicAuthorization
```
```

A type that allows you to request the user’s informed consent for your app to access their music data.
```

### [Apple Music Subscription](/documentation/MusicKit#Apple-Music-Subscription)

```swift
```swift
```swift
```swift
struct MusicSubscription
```
```

A representation of the current state of the user’s subscription to Apple Music.
```
```swift
```swift
```swift
struct MusicSubscriptionOffer
```
```

A type for grouping other types for showing subscription offers for Apple Music.
```
```

### [Token management](/documentation/MusicKit#Token-management)

The framework manages tokens for accessing Apple Music API automatically by default, but you can generate your own developer token by creating a class that inherits from the token provider type alias.

```swift
```swift
```swift
typealias MusicTokenProvider
```
```

An object that music requests use to access Apple Music API.
```
```swift
```swift
```swift
protocol MusicDeveloperTokenProvider
```
```

A set of methods that music requests use to access Apple Music API.
```
```swift
```swift
```swift
class MusicUserTokenProvider
```
```

A class that music requests use to fetch user tokens your app requires to access Apple Music API.
```
```swift
```swift
```swift
struct MusicTokenRequestOptions
```
```

Options that music requests pass into token provider methods to fetch a required token for accessing Apple Music API.
```
```swift
```swift
```swift
enum MusicTokenRequestError
```
```

An error that the token provider or music requests can throw upon requesting any token necessary for accessing Apple Music API.
```
```swift
```swift
```swift
class DefaultMusicTokenProvider
```
```

The default token provider that music requests use to access Apple Music API.
```

### [Utility](/documentation/MusicKit#Utility)

```swift
```swift
```swift
```swift
protocol MusicItem
```
```

A protocol with basic requirements for music items.
```
```swift
```swift
```swift
struct MusicItemID
```
```

An object that represents a unique identifier for a music item.
```
```swift
```swift
```swift
struct MusicItemCollection
```
```

A collection of music items.
```
```swift
```swift
```swift
protocol MusicPropertyContainer
```
```

A protocol for music items that allow loading additional properties that you can fetch asynchronously.
```
```swift
```swift
```swift
class MusicRelationshipProperty
```
```

An identifier for a music item relationship property from a specific root type to a specific value type for the element of the resulting collection.
```
```swift
```swift
```swift
class MusicExtendedAttributeProperty
```
```

An identifier for a music item extended attribute property from a specific root type to a specific resulting value type.
```
```swift
```swift
```swift
class MusicAttributeProperty
```
```

An identifier for a music item attribute property from a specific root type to a specific resulting value type.
```
```swift
```swift
```swift
class PartialMusicAsyncProperty
```
```

A partially type-erased identifier for a music item property that you can fetch asynchronously from a concrete root type to any resulting value type.
```
```swift
```swift
```swift
class PartialMusicProperty
```
```

A partially type-erased identifier for a music item property from a concrete root type to any resulting value type.
```
```swift
```swift
```swift
class AnyMusicProperty
```
```

A type-erased identifier for a music item property, from any root type to any resulting value type.
```
```

### [Classes](/documentation/MusicKit#Classes)

```swift
```swift
```swift
```swift
class MusicLibrary
```
```

An object your app uses to access the user’s music library.
```
```

### [Protocols](/documentation/MusicKit#Protocols)

```swift
```swift
```swift
```swift
protocol LibraryAlbumFilter
```
```

Album properties your app uses as a filter for a library request.
```
```swift
```swift
```swift
protocol LibraryAlbumSortProperties
```
```

Album properties your app uses to sort results for a library request.
```
```swift
```swift
```swift
protocol LibraryArtistFilter
```
```

Artist properties your app uses as a filter for a library request.
```
```swift
```swift
```swift
protocol LibraryArtistSortProperties
```
```

Artist properties your app uses to sort results for a library request.
```
```swift
```swift
```swift
protocol LibraryGenreFilter
```
```

Genre properties your app uses as a filter for a library request.
```
```swift
```swift
```swift
protocol LibraryGenreSortProperties
```
```

Genre properties your app uses to sort results for a library request.
```
```swift
```swift
```swift
protocol LibraryMusicVideoFilter
```
```

Music video properties your app uses as a filter for a library request.
```
```swift
```swift
```swift
protocol LibraryMusicVideoSortProperties
```
```

Music video properties your app uses to sort results for a library request.
```
```swift
```swift
```swift
protocol LibraryPlaylistEntryFilter
```
```

Playlist entry properties your app uses as a filter for a library request.
```
```swift
```swift
```swift
protocol LibraryPlaylistEntrySortProperties
```
```

Playlist entry properties your app uses to sort results for a library request.
```
```swift
```swift
```swift
protocol LibraryPlaylistFilter
```
```

Playlist properties your app uses as a filter for a library request.
```
```swift
```swift
```swift
protocol LibraryPlaylistSortProperties
```
```

Playlist properties your app uses to sort results for a library request.
```
```swift
```swift
```swift
protocol LibrarySongFilter
```
```

Song properties your app uses as a filter for a library request.
```
```swift
```swift
```swift
protocol LibrarySongSortProperties
```
```

Song properties your app uses to sort results for a library request.
```
```swift
```swift
```swift
protocol LibraryTrackFilter
```
```

Track properties your app uses as a filter for a library request.
```
```swift
```swift
```swift
protocol LibraryTrackSortProperties
```
```

Track properties your app uses to sort results for a library request.
```
```swift
```swift
```swift
protocol MusicCatalogChartRequestable
```
```

A protocol for music items that your app can fetch by using a catalog charts request.
```
```swift
```swift
```swift
protocol MusicCatalogTopLevelResourceRequesting
```
```

A protocol for music items that your app can fetch by using a catalog resource request without any filter.
```
```swift
```swift
```swift
protocol MusicLibraryAddable
```
```

A protocol for music items that your app can add to the music library.
```
```swift
```swift
```swift
protocol MusicLibraryRequestFilterValueEquatable
```
```

A protocol for types of values your app can use with equality filters when fetching items using a music library request.
```
```swift
```swift
```swift
protocol MusicLibraryRequestFilterValueMembershipComparable
```
```

A protocol for types of values your app can use with membership filters when fetching items using a music library request.
```
```swift
```swift
```swift
protocol MusicLibraryRequestable
```
```

A protocol for music items that your app can fetch by using a library request.
```
```swift
```swift
```swift
protocol MusicLibrarySearchable
```
```

A protocol for music items that your app can fetch by using a library search request.
```
```swift
```swift
```swift
protocol MusicLibrarySectionRequestable
```
```

A protocol for types your app uses as sections when fetching items using a library sectioned request.
```
```swift
```swift
```swift
protocol MusicPersonalRecommendationItem
```
```

A protocol for music items that your app can fetch by using a personal recommendations request.
```
```swift
```swift
```swift
protocol MusicPlaylistAddable
```
```

A protocol for music items that your app can add to a playlist.
```
```swift
```swift
```swift
protocol MusicRecentlyPlayedRequestable
```
```

A protocol for music items that your app can fetch by using a recently played request.
```
```

### [Structures](/documentation/MusicKit#Structures)

```swift
```swift
```swift
```swift
struct MusicCatalogChart
```
```

An object that contains popular items in the Apple Music catalog.
```
```swift
```swift
```swift
struct MusicCatalogChartsRequest
```
```

A request that your app uses to fetch the most popular items in the Apple Music catalog.
```
```swift
```swift
```swift
struct MusicCatalogChartsResponse
```
```

An object that contains results for a catalog charts request.
```
```swift
```swift
```swift
struct MusicCatalogSearchSuggestionsRequest
```
```

A request that your app uses to fetch suggestions from the Apple Music catalog using a search term.
```
```swift
```swift
```swift
struct MusicCatalogSearchSuggestionsResponse
```
```

An object that contains results for a catalog search suggestions request.
```
```swift
```swift
```swift
struct MusicLibraryRequest
```
```

A request that your app uses to fetch items from the user’s music library.
```
```swift
```swift
```swift
struct MusicLibraryResponse
```
```

An object that contains results for a library request.
```
```swift
```swift
```swift
struct MusicLibrarySearchRequest
```
```

A request that your app uses to fetch items from user’s library using a search term.
```
```swift
```swift
```swift
struct MusicLibrarySearchResponse
```
```

An object that contains results for a library search request.
```
```swift
```swift
```swift
struct MusicLibrarySection
```
```

A section for a library sectioned response.
```
```swift
```swift
```swift
struct MusicLibrarySectionedRequest
```
```

A request that your app uses to fetch items grouped by sections from the user’s music library.
```
```swift
```swift
```swift
struct MusicLibrarySectionedResponse
```
```

An object that contains results for a library sectioned request.
```
```swift
```swift
```swift
struct MusicPersonalRecommendation
```
```

An object that contains recommended items based on the user’s library and listening history.
```
```swift
```swift
```swift
struct MusicPersonalRecommendationsRequest
```
```

A request that your app uses to fetch music recommendations based on the user’s library and listening history.
```
```swift
```swift
```swift
struct MusicPersonalRecommendationsResponse
```
```

An object that contains results for a personal recommendations request.
```
```swift
```swift
```swift
struct MusicRecentlyPlayedRequest
```
```

A request that your app uses to fetch items the user has recently played.
```
```swift
```swift
```swift
struct MusicRecentlyPlayedResponse
```
```

An object that contains items the user has recently played.
```
```swift
```swift
```swift
struct TitledSection
```
```

A section you can use to request items from the library grouped by title.
```
```

### [Type Aliases](/documentation/MusicKit#Type-Aliases)

```swift
```swift
```swift
```swift
typealias MusicRecentlyPlayedContainerRequest
```
```

A request that your app uses to fetch albums, playlists or stations that the user has recently played.
```
```swift
```swift
```swift
typealias MusicRecentlyPlayedContainerResponse
```
```

An object that contains albums, playlists or stations that the user has recently played.
```
```

### [Enumerations](/documentation/MusicKit#Enumerations)

```swift
```swift
```swift
```swift
enum AudioVariant
```
```

Variants that indicate the quality of audio available for an item.
```
```swift
```swift
```swift
enum MusicCatalogChartKind
```
```

The available kinds of catalog charts.
```
```swift
```swift
```swift
enum MusicPropertySource
```
```

An enumeration that specifies which source to use when requesting properties and relationships.
```
```swift
```swift
```swift
enum RecentlyPlayedMusicItem
```
```

An item that represents an album, a playlist, or a station that the user has recently played.
```
```

## [See Also](/documentation/MusicKit#see-also)

### [Related Documentation](/documentation/MusicKit#Related-Documentation)

[

Media Player](/documentation/MediaPlayer)

Find and play songs, audio podcasts, audio books, and more from within your app.

[

Apple Music API](/documentation/AppleMusicAPI)

Integrate streaming music with catalog and personal content.