

- Apple Music Feed
-  Album 

Object

# Album

The data structure that represents an Album resource.

AppleMusicFeed 1.0+

``` source
object Album
```

## Properties

`albumType`

`string`

The type of the album. The possible values are `standard`, `single`, `deluxe`, `compilation`, and `ep`.

`artistRoles`

`[`Album.ArtistRole`]`

**(Required)** A list of artists and their roles.

`artworks`

Album.Artworks

**(Required)** A mapping of locale to localized album cover art.

`contentProvider`

`string`

The name of the company that provides the album. Don’t use this name for display purposes. This name doesn’t display in Apple Music.

`contentTraits`

`[string]`

**(Required)** A list of the content traits for the album. The possible values are `remix`, `live`, `compilation`, and `karaoke`.

`copyright`

`string`

The copyright notice text.

`copyrightPline`

`string`

The copyright performance rights text that displays in Apple Music.

`featuredArtists`

`[`Album.RelatedArtist`]`

**(Required)** A list of featured artists for the album.

`genres`

`[`Album.Genre`]`

**(Required)** A list of genre information for the album.

`id`

`string`

The identifier for the album in Apple Music.

`lastModifiedTime`

`string`

The time, in ISO 8601 format, of the entity’s most recent update.

`name`

Album.Name

**(Required)** A mapping of locale to localized uncensored names for the album.

`nameDefault`

`string`

The default name for the album.

`namePronunciation`

Album.NamePronunciation

**(Required)** A mapping of locale to translations for the specific pronunciation-name translation type.

`parentalAdvisoryType`

`string`

The type of parental advisory status. The possible values are `none`, `explicit`, `not explicit`, and `cleaned`.

`prices`

Album.Prices

**(Required)** A mapping of locale to pricing information. Pricing offer parameters include `price`, `priceType`, and `quality`.

`primaryArtists`

`[`Album.RelatedArtist`]`

**(Required)** A list of the primary artists of the album.

`recordLabels`

`[`Album.RecordLabel`]`

**(Required)** A list of record labels for the album.

`releaseDate`

Album.ReleaseDate

**(Required)** A mapping of locale to release date, in YYYY-MM-DD format.

`songs`

`[`Album.RelatedSong`]`

**(Required)** A list of songs in the album.

`titleVersion`

Album.TitleVersion

**(Required)** A mapping of locale to translations for the specific title-version translation type.

`titleVersionPronunciation`

Album.TitleVersionPronunciation

**(Required)** A mapping of locale to translations for the specific title-version-pronunciation-name translation type.

`upc`

`string`

The Universal Product Code or European Article Number for a piece of content from the provider.

`urlTemplate`

`string`

A template for the URL to view the entity in Apple Music. The template requires an ISO country code for the `{country-code}` placeholder.

## Attributes 

Possible types:

## Topics

### Related objects

object Album.ArtistRole

Information about an artist’s role.

object Album.Artworks

A mapping of locale to localized album cover art.

object Album.Genre

A genre name and its structure.

object Album.Name

A mapping of locale to localized names for the album.

object Album.NamePronunciation

A mapping of locale to translations for the specific pronunciation-name translation type.

object Album.Prices

A mapping of locale to pricing information.

object Album.RecordLabel

Information about a record label.

object Album.RelatedArtist

Information about a related artist.

object Album.RelatedSong

Information about a related song.

object Album.ReleaseDate

A mapping of locale to release date for the album.

object Album.TitleVersion

A mapping of locale to translations for the specific title-version translation type.

object Album.TitleVersionPronunciation

A mapping of locale to translations for the specific title-version-pronunciation-name translation type.

## See Also

### Objects

object Song

The data structure that represents a Song resource.

object Artist

The data structure that represents an Artist resource.

object PopularityTopChartAlbums

The data structure that represents an album popularity chart resource.

object PopularityTopChartSongs

The data structure that represents a song popularity chart resource.

