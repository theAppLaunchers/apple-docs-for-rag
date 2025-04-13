

- Apple Music API
-  Get Recently Added Resources 

Web Service Endpoint

# Get Recently Added Resources

Fetch the resources recently added to the library.

Apple Music 1.0+

## URL

``` source
GET https://api.music.apple.com/v1/me/library/recently-added
```

## Query Parameters

`l`

`string`

The localization to use, specified by a language tag. The possible values are in the `supportedLanguageTags` array belonging to the `Storefront` object specified by `storefront`. Otherwise, the default is `defaultLanguageTag` in `Storefront`.

## Response Codes

` 200 ``OK`

ResourceCollectionResponse

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
https://api.music.apple.com/v1/me/library/recently-added
```

```
{    
    "next": "/v1/me/library/recently-added?offset=10",
    "data": [
        {
            "id": "l.NWqWi1m",
            "type": "library-albums",
            "href": "/v1/me/library/albums/l.NWqWi1m",
            "attributes": {
                "artistName": "Elephante",
                "genreNames": [
                    "Electronic"
                ],
                "playParams": {
                    "id": "l.NWqWi1m",
                    "kind": "album",
                    "isLibrary": true
                },
                "dateAdded": "2021-10-06T16: 47: 33Z",
                "artwork": {
                    "width": 1200,
                    "height": 1200,
                    "url": "https: //is1-ssl.mzstatic.com/image/thumb/Music115/v4/76/15/f3/7615f398-b97c-0df7-e840-2d45c14c4f60/190296481482.jpg/{w}x{h}bb.jpg"
                },
                "name": "Dopamine - Single",
                "trackCount": 1,
                "releaseDate": "2021-10-01"
            }
        },
        {
            "id": "l.KPXJEO4",
            "type": "library-albums",
            "href": "/v1/me/library/albums/l.KPXJEO4",
            "attributes": {
                "artistName": "James Arthur",
                "genreNames": [
                    "Pop"
                ],
                "playParams": {
                    "id": "l.KPXJEO4",
                    "kind": "album",
                    "isLibrary": true
                },
                "dateAdded": "2021-10-05T21: 40: 11Z",
                "artwork": {
                    "width": 1200,
                    "height": 1200,
                    "url": "https: //is5-ssl.mzstatic.com/image/thumb/Music115/v4/f2/9e/3a/f29e3a22-ed78-a55c-97d6-d56def0bef25/886449290833.jpg/{w}x{h}bb.jpg"
                },
                "name": "September - Single",
                "trackCount": 1,
                "releaseDate": "2021-06-11"
            }
        },
        {
            "id": "l.REWyBL8",
            "type": "library-albums",
            "href": "/v1/me/library/albums/l.REWyBL8",
            "attributes": {
                "artistName": "Jess Glynne",
                "genreNames": [
                    "Pop"
                ],
                "playParams": {
                    "id": "l.REWyBL8",
                    "kind": "album",
                    "isLibrary": true
                },
                "dateAdded": "2021-10-05T06: 18: 27Z",
                "artwork": {
                    "width": 1200,
                    "height": 1200,
                    "url": "https: //is2-ssl.mzstatic.com/image/thumb/Music124/v4/2f/95/12/2f95123c-6fb0-055d-f018-a540f22848c6/190295416836.jpg/{w}x{h}bb.jpg"
                },
                "name": "Always in Between (Deluxe)",
                "trackCount": 1,
                "releaseDate": "2018-05-04"
            }
        },
        {
            "id": "l.FH0ZX5z",
            "type": "library-albums",
            "href": "/v1/me/library/albums/l.FH0ZX5z",
            "attributes": {
                "artistName": "Culture Code & Alexis Donn",
                "genreNames": [
                    "Electronic"
                ],
                "playParams": {
                    "id": "l.FH0ZX5z",
                    "kind": "album",
                    "isLibrary": true
                },
                "dateAdded": "2021-10-03T17: 32: 40Z",
                "artwork": {
                    "width": 1200,
                    "height": 1200,
                    "url": "https: //is2-ssl.mzstatic.com/image/thumb/Music125/v4/d7/dd/6d/d7dd6d15-0265-12d5-02f0-5200a48bd715/cover.jpg/{w}x{h}bb.jpg"
                },
                "name": "You & I - Single",
                "trackCount": 1,
                "releaseDate": "2021-08-26"
            }
        },
        {
            "id": "p.WmzVKBLFxprx0E",
            "type": "library-playlists",
            "href": "/v1/me/library/playlists/p.WmzVKBLFxprx0E",
            "attributes": {
                "playParams": {
                    "id": "p.WmzVKBLFxprx0E",
                    "kind": "playlist",
                    "isLibrary": true,
                    "globalId": "pl.9dc9de535a544d5d9692766feac0f7c7"
                },
                "isPublic": false,
                "dateAdded": "2021-09-29T19: 09: 24Z",
                "name": "Permanent Vacation",
                "description": {
                    "standard": "The soundtrack to your next escape—even if you’re staying put."
                },
                "hasCatalog": true,
                "artwork": {
                    "width": null,
                    "height": null,
                    "url": "https: //is3-ssl.mzstatic.com/image/thumb/Features125/v4/cd/47/f9/cd47f91a-e318-bdb2-7293-a76e484a50ae/contsched.tunnffvr.png/{w}x{h}SC.DN01.jpg"
                },
                "canEdit": false
            }
        },
        {
            "id": "l.G8wMn6w",
            "type": "library-albums",
            "href": "/v1/me/library/albums/l.G8wMn6w",
            "attributes": {
                "artistName": "Dua Lipa",
                "genreNames": [
                    "Pop"
                ],
                "playParams": {
                    "id": "l.G8wMn6w",
                    "kind": "album",
                    "isLibrary": true
                },
                "dateAdded": "2021-09-29T18: 27: 45Z",
                "artwork": {
                    "width": 1200,
                    "height": 1200,
                    "url": "https: //is5-ssl.mzstatic.com/image/thumb/Video124/v4/3f/1e/6f/3f1e6f35-6960-3f0e-0a0c-8701aa2012d4/dj.bcvxpufw.jpg/{w}x{h}bb.jpg"
                },
                "name": "Unknown Album",
                "trackCount": 1,
                "releaseDate": "2021-02-12"
            }
        },
        {
            "id": "l.8mDKroj",
            "type": "library-albums",
            "href": "/v1/me/library/albums/l.8mDKroj",
            "attributes": {
                "artistName": "Man Cub",
                "genreNames": [
                    "Dance"
                ],
                "playParams": {
                    "id": "l.8mDKroj",
                    "kind": "album",
                    "isLibrary": true
                },
                "dateAdded": "2021-09-28T05: 50: 24Z",
                "artwork": {
                    "width": 1200,
                    "height": 1200,
                    "url": "https: //is3-ssl.mzstatic.com/image/thumb/Music123/v4/35/a6/17/35a617bd-4d83-b9e5-92cd-ea8618c27402/5054285157053.png/{w}x{h}bb.jpg"
                },
                "name": "Impressions",
                "trackCount": 1,
                "releaseDate": "2020-06-12"
            }
        },
        {
            "id": "l.dsZCeEv",
            "type": "library-albums",
            "href": "/v1/me/library/albums/l.dsZCeEv",
            "attributes": {
                "artistName": "GhostDragon",
                "genreNames": [
                    "Electronic"
                ],
                "playParams": {
                    "id": "l.dsZCeEv",
                    "kind": "album",
                    "isLibrary": true
                },
                "dateAdded": "2021-09-24T02: 14: 11Z",
                "artwork": {
                    "width": 1200,
                    "height": 1200,
                    "url": "https: //is5-ssl.mzstatic.com/image/thumb/Music114/v4/33/2a/69/332a69ba-b687-ecaa-6a27-9ce5ed0e2492/cover.jpg/{w}x{h}bb.jpg"
                },
                "name": "Stories - EP",
                "trackCount": 2,
                "releaseDate": "2020-03-14"
            }
        },
        {
            "id": "l.F6QVDFo",
            "type": "library-albums",
            "href": "/v1/me/library/albums/l.F6QVDFo",
            "attributes": {
                "artistName": "Monstercat",
                "genreNames": [
                    "Dance"
                ],
                "playParams": {
                    "id": "l.F6QVDFo",
                    "kind": "album",
                    "isLibrary": true
                },
                "dateAdded": "2021-09-24T20: 57: 21Z",
                "artwork": {
                    "width": 1200,
                    "height": 1200,
                    "url": "https: //is1-ssl.mzstatic.com/image/thumb/Music114/v4/c9/ad/36/c9ad3692-027f-046a-313b-40b487e4c949/742779537072.png/{w}x{h}bb.jpg"
                },
                "name": "Monstercat Instinct Vol. 7",
                "trackCount": 1,
                "releaseDate": "2021-03-09"
            }
        },
        {
            "id": "l.ndPcyOd",
            "type": "library-albums",
            "href": "/v1/me/library/albums/l.ndPcyOd",
            "attributes": {
                "artistName": "The Kid LAROI",
                "genreNames": [
                    "Pop"
                ],
                "playParams": {
                    "id": "l.ndPcyOd",
                    "kind": "album",
                    "isLibrary": true
                },
                "dateAdded": "2021-09-24T19: 14: 17Z",
                "artwork": {
                    "width": 1200,
                    "height": 1200,
                    "url": "https: //is4-ssl.mzstatic.com/image/thumb/Music125/v4/9d/69/f1/9d69f15c-7bcc-24e9-0adc-ec3afd0bf5cc/886449473663.jpg/{w}x{h}bb.jpg"
                },
                "name": "F*CK LOVE 3+: OVER YOU",
                "trackCount": 1,
                "releaseDate": "2020-07-22"
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

Get Recently Played Tracks

Fetch the recently played tracks for the user.

Get Recently Played Stations

Fetch recently played radio stations for the user.

