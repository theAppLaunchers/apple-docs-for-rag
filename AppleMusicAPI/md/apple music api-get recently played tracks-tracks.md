

- Apple Music API
-  Get Recently Played Tracks 

Web Service Endpoint

# Get Recently Played Tracks

Fetch the recently played tracks for the user.

Apple Music 1.0+

## URL

``` source
GET https://api.music.apple.com/v1/me/recent/played/tracks
```

## Query Parameters

`include`

`[string]`

Additional relationships to include in the fetch.

`l`

`string`

The localization to use, specified by a language tag. The possible values are in the `supportedLanguageTags` array belonging to the `Storefront` object specified by `storefront`. Otherwise, the default is `defaultLanguageTag` in `Storefront`.

`limit`

`integer`

The maximum number of recently played tracks to return.

Default: `30`

Maximum: `30`

`offset`

`string`

The offset to use for a paginated request.

`extend`

`[string]`

A list of attribute extensions to apply to resources in the response.

`types`

`[string]`

 (Required) 

The track types to include in the response.

Possible Values: `library-music-videos, library-songs, music-videos, songs`

## Response Codes

` 200 ``OK`

PaginatedResourceCollectionResponse

`OK`

The request was successful.

Content-Type: application/json

` 401 ``Unauthorized`

UnauthorizedResponse

`Unauthorized`

A response indicating an incorrect `Authorization` header.

Content-Type: application/json

` 403 ``Forbidden`

ForbiddenResponse

`Forbidden`

A response indicating invalid or insufficient authentication.

Content-Type: application/json

` 500 ``Internal Server Error`

ErrorsResponse

`Internal Server Error`

A response indicating an error occurred on the server.

Content-Type: application/json

## Discussion

If successful, the HTTP status code is 200 (OK) and the `data` array contains an array of Resource objects. If unsuccessful, the HTTP status code indicates the error and the details are in the `errors` array. For more information, see Handling Requests and Responses.

This endpoint requires a music user token. For more information, see User Authentication for MusicKit.

### Example

- Request
- Response

```
https://api.music.apple.com/v1/me/recent/played/tracks
```

```
{
  "data": [
    {
      "id": "1622045954",
      "type": "songs",
      "href": "/v1/catalog/us/songs/1622045954",
      "attributes": {
        "albumName": "Un Verano Sin Ti",
        "genreNames": [
          "Latin",
          "Music"
        ],
        "trackNumber": 10,
        "durationInMillis": 213061,
        "releaseDate": "2022-05-06",
        "isrc": "QM6MZ2214884",
        "artwork": {
          "width": 3000,
          "height": 3000,
          "url": "https://is5-ssl.mzstatic.com/image/thumb/Music112/v4/3e/04/eb/3e04ebf6-370f-f59d-ec84-2c2643db92f1/196626945068.jpg/{w}x{h}bb.jpg",
          "bgColor": "fcc2c1",
          "textColor1": "170a0b",
          "textColor2": "21201e",
          "textColor3": "452f2f",
          "textColor4": "4d403e"
        },
        "composerName": "Benito Antonio Martínez Ocasio",
        "url": "https://music.apple.com/us/album/efecto/1622045624?i=1622045954",
        "playParams": {
          "id": "1622045954",
          "kind": "song"
        },
        "discNumber": 1,
        "hasLyrics": true,
        "isAppleDigitalMaster": false,
        "name": "Efecto",
        "previews": [
          {
            "url": "https://audio-ssl.itunes.apple.com/itunes-assets/AudioPreview112/v4/c1/07/c9/c107c972-3943-f907-362a-77f13240759a/mzaf_3784396904364056475.plus.aac.p.m4a"
          }
        ],
        "artistName": "Bad Bunny"
      }
    },
    {
      "id": "1613600188",
      "type": "songs",
      "href": "/v1/catalog/us/songs/1613600188",
      "attributes": {
        "albumName": "Emotional Creature",
        "genreNames": [
          "Alternative",
          "Music"
        ],
        "trackNumber": 1,
        "durationInMillis": 221000,
        "releaseDate": "2022-06-09",
        "isrc": "USQE92100257",
        "artwork": {
          "width": 3000,
          "height": 3000,
          "url": "https://is1-ssl.mzstatic.com/image/thumb/Music112/v4/df/4e/68/df4e6833-9828-51d7-cdeb-71ecf6d3a23d/810090090962.png/{w}x{h}bb.jpg",
          "bgColor": "202020",
          "textColor1": "aea6f6",
          "textColor2": "b68ef6",
          "textColor3": "918bcb",
          "textColor4": "9878cb"
        },
        "composerName": "Anthony Vaccaro, Jon Alvarado, Lili Trifilio & Matt Henkels",
        "url": "https://music.apple.com/us/album/entropy/1613600183?i=1613600188",
        "playParams": {
          "id": "1613600188",
          "kind": "song"
        },
        "discNumber": 1,
        "hasLyrics": true,
        "isAppleDigitalMaster": true,
        "name": "Entropy",
        "previews": [
          {
            "url": "https://audio-ssl.itunes.apple.com/itunes-assets/AudioPreview122/v4/f3/bc/f4/f3bcf45a-fb91-b87c-e6b3-a7d91edb817d/mzaf_10050745656465536755.plus.aac.p.m4a"
          }
        ],
        "artistName": "Beach Bunny"
      }
    },
    {
      "id": "1605983206",
      "type": "songs",
      "href": "/v1/catalog/us/songs/1605983206",
      "attributes": {
        "albumName": "Palaces",
        "genreNames": [
          "Electronic",
          "Music",
          "Dance"
        ],
        "trackNumber": 6,
        "releaseDate": "2022-05-20",
        "durationInMillis": 254868,
        "isrc": "AUFF02200006",
        "artwork": {
          "width": 4000,
          "height": 4000,
          "url": "https://is5-ssl.mzstatic.com/image/thumb/Music112/v4/ce/8c/7b/ce8c7bc8-e070-7faa-1d58-157e4550e483/653738991029.png/{w}x{h}bb.jpg",
          "bgColor": "e19c27",
          "textColor1": "040807",
          "textColor2": "321604",
          "textColor3": "30250d",
          "textColor4": "55300b"
        },
        "composerName": "Harley Streten",
        "playParams": {
          "id": "1605983206",
          "kind": "song"
        },
        "url": "https://music.apple.com/us/album/get-u/1605983198?i=1605983206",
        "discNumber": 1,
        "hasLyrics": false,
        "isAppleDigitalMaster": false,
        "name": "Get U",
        "previews": [
          {
            "url": "https://audio-ssl.itunes.apple.com/itunes-assets/AudioPreview122/v4/0c/bf/1a/0cbf1aa3-6296-7d8f-7230-9d6364ebdc73/mzaf_2382622098990779659.plus.aac.p.m4a"
          }
        ],
        "artistName": "Flume"
      }
    }
  ]
}
```

## See Also

### Related Documentation

object Resource

A resource—such as an album, song, or playlist.

### Requesting Historical Information

Get Heavy Rotation Content

Fetch the resources in heavy rotation for the user.

Get Recently Played Resources

Fetch the recently played resources for the user.

Get Recently Played Stations

Fetch recently played radio stations for the user.

Get Recently Added Resources

Fetch the resources recently added to the library.

