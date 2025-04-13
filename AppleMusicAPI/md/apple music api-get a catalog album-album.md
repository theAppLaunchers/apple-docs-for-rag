

- Apple Music API
-  Get a Catalog Album 

Web Service Endpoint

# Get a Catalog Album

Fetch an album by using its identifier.

Apple Music 1.0+

## URL

``` source
GET https://api.music.apple.com/v1/catalog/{storefront}/albums/{id}
```

## Path Parameters

`id`

`string`

 (Required) 

The unique identifier for the album.

`storefront`

`string`

 (Required) 

An iTunes Store territory, specified by an ISO 3166 alpha-2 country code. The possible values are the `id` attributes of `Storefront` objects.

## Query Parameters

`l`

`string`

The localization to use, specified by a language tag. The possible values are in the `supportedLanguageTags` array belonging to the `Storefront` object specified by `storefront`. Otherwise, the default is `defaultLanguageTag` in `Storefront`.

`include`

`[string]`

Additional relationships to include in the fetch.

`views`

`[string]`

The views to activate for the albums resource.

Possible Values: `appears-on, other-versions, related-albums, related-videos`

`extend`

`[string]`

A list of attribute extensions to apply to resources in the response.

## Response Codes

` 200 ``OK`

AlbumsResponse

`OK`

The request was successful.

Content-Type: application/json

` 401 ``Unauthorized`

UnauthorizedResponse

`Unauthorized`

A response indicating an incorrect `Authorization` header.

Content-Type: application/json

` 500 ``Internal Server Error`

ErrorsResponse

`Internal Server Error`

A response indicating an error occurred on the server.

Content-Type: application/json

## Discussion

If successful, the HTTP status code is 200 (OK) and the `data` array contains the requested resource object. If unsuccessful, the HTTP status code indicates the error and the details are in the `errors` array. For more information, see Handling Requests and Responses.

### Example

- Request
- Response

```
https://api.music.apple.com/v1/catalog/us/albums/1616728060
```

```
{
    "data": [
        {
            "id": "1616728060",
            "type": "albums",
            "href": "/v1/catalog/us/albums/1616728060",
            "attributes": {
                "copyright": "A 10 Summers/Interscope Records Release; ℗ 2022 10 Summers Records, LLC",
                "genreNames": [
                    "R&B/Soul",
                    "Music"
                ],
                "releaseDate": "2022-05-06",
                "upc": "00602445790951",
                "isMasteredForItunes": true,
                "artwork": {
                    "width": 3000,
                    "height": 3000,
                    "url": "https://is3-ssl.mzstatic.com/image/thumb/Music112/v4/03/45/19/034519dc-9ff9-7f63-3d02-23a101a0cc3a/22UMGIM01299.rgb.jpg/{w}x{h}bb.jpg",
                    "bgColor": "0b1b18",
                    "textColor1": "fc977a",
                    "textColor2": "ef5429",
                    "textColor3": "cc7e66",
                    "textColor4": "c14925"
                },
                "playParams": {
                    "id": "1616728060",
                    "kind": "album"
                },
                "url": "https://music.apple.com/us/album/heart-on-my-sleeve/1616728060",
                "recordLabel": "10 Summers/Interscope Records",
                "isCompilation": false,
                "trackCount": 15,
                "isSingle": false,
                "name": "Heart On My Sleeve",
                "contentRating": "explicit",
                "artistName": "Ella Mai",
                "editorialNotes": {
                    "standard": "Ella Mai knows her way around a love song. We've known that for years—certainly since her 2017 single “Boo'd Up” proved a breakout sensation—but her second album cements her as one of R&B's preeminent heart healers. Heart on My Sleeve is filled with the kind of desperate pleas and resolute statements of adoration that could soften even the hardest of hearts. With a voice made of satin and honey, she sings of love in the way so many wish to feel it—vulnerable and terrified yet thoroughly convinced it's worth it...",
                    "short": "The singer dazzles with her second LP, a collection of lush, heartfelt R&B."
                },
                "isComplete": true
            },
            "relationships": {
                "artists": {
                    "href": "/v1/catalog/us/albums/1616728060/artists",
                    "data": [
                        {
                            "id": "1160482144",
                            "type": "artists",
                            "href": "/v1/catalog/us/artists/1160482144"
                        }
                    ]
                },
                "tracks": {
                    "href": "/v1/catalog/us/albums/1616728060/tracks",
                    "data": [
                        {
                            "id": "1616728064",
                            "type": "songs",
                            "href": "/v1/catalog/us/songs/1616728064",
                            "attributes": {
                                "albumName": "Heart On My Sleeve",
                                "genreNames": [
                                    "R&B/Soul",
                                    "Music"
                                ],
                                "trackNumber": 1,
                                "releaseDate": "2022-05-06",
                                "durationInMillis": 197314,
                                "isrc": "USUM72203653",
                                "artwork": {
                                    "width": 3000,
                                    "height": 3000,
                                    "url": "https://is3-ssl.mzstatic.com/image/thumb/Music112/v4/03/45/19/034519dc-9ff9-7f63-3d02-23a101a0cc3a/22UMGIM01299.rgb.jpg/{w}x{h}bb.jpg",
                                    "bgColor": "0b1b18",
                                    "textColor1": "fc977a",
                                    "textColor2": "ef5429",
                                    "textColor3": "cc7e66",
                                    "textColor4": "c14925"
                                },
                                "composerName": "Charles Hinshaw Jr, Dijon McFarlane, Ella Mai Howell, NICHOLAS MATTHEW BALDING, Peter Johnson & Shah Rukh Zaman Khan",
                                "playParams": {
                                    "id": "1616728064",
                                    "kind": "song"
                                },
                                "url": "https://music.apple.com/us/album/trying/1616728060?i=1616728064",
                                "discNumber": 1,
                                "isAppleDigitalMaster": true,
                                "hasLyrics": true,
                                "name": "Trying",
                                "previews": [
                                    {
                                        "url": "https://audio-ssl.itunes.apple.com/itunes-assets/AudioPreview112/v4/c8/99/a7/c899a79c-e0b1-68ff-ac5e-37cb41c8bc6a/mzaf_613689503757681664.plus.aac.p.m4a"
                                    }
                                ],
                                "artistName": "Ella Mai"
                            }
                        },
                        {
                            "id": "1616728065",
                            "type": "songs",
                            "href": "/v1/catalog/us/songs/1616728065",
                            "attributes": {
                                "albumName": "Heart On My Sleeve",
                                "genreNames": [
                                    "R&B/Soul",
                                    "Music"
                                ],
                                "trackNumber": 2,
                                "durationInMillis": 255013,
                                "releaseDate": "2022-04-02",
                                "isrc": "USUM72203647",
                                "artwork": {
                                    "width": 3000,
                                    "height": 3000,
                                    "url": "https://is3-ssl.mzstatic.com/image/thumb/Music112/v4/03/45/19/034519dc-9ff9-7f63-3d02-23a101a0cc3a/22UMGIM01299.rgb.jpg/{w}x{h}bb.jpg",
                                    "bgColor": "0b1b18",
                                    "textColor1": "fc977a",
                                    "textColor2": "ef5429",
                                    "textColor3": "cc7e66",
                                    "textColor4": "c14925"
                                },
                                "composerName": "Jahaan Sweet, Matthew Samuels, Khristopher Riddick-Tynes, Leon Thomas III, Ella Mai Howell & Varren Wade",
                                "url": "https://music.apple.com/us/album/not-another-love-song/1616728060?i=1616728065",
                                "playParams": {
                                    "id": "1616728065",
                                    "kind": "song"
                                },
                                "discNumber": 1,
                                "hasLyrics": true,
                                "isAppleDigitalMaster": true,
                                "name": "Not Another Love Song",
                                "previews": [
                                    {
                                        "url": "https://audio-ssl.itunes.apple.com/itunes-assets/AudioPreview122/v4/c2/01/ad/c201ad8c-9597-9eae-1013-0694c393be2e/mzaf_10993214544239266867.plus.aac.p.m4a"
                                    }
                                ],
                                "artistName": "Ella Mai"
                            }
                        },
                        {
                            "id": "1616728066",
                            "type": "songs",
                            "href": "/v1/catalog/us/songs/1616728066",
                            "attributes": {
                                "albumName": "Heart On My Sleeve",
                                "genreNames": [
                                    "R&B/Soul",
                                    "Music"
                                ],
                                "trackNumber": 3,
                                "releaseDate": "2022-05-06",
                                "durationInMillis": 245650,
                                "isrc": "USUM72203642",
                                "artwork": {
                                    "width": 3000,
                                    "height": 3000,
                                    "url": "https://is3-ssl.mzstatic.com/image/thumb/Music112/v4/03/45/19/034519dc-9ff9-7f63-3d02-23a101a0cc3a/22UMGIM01299.rgb.jpg/{w}x{h}bb.jpg",
                                    "bgColor": "0b1b18",
                                    "textColor1": "fc977a",
                                    "textColor2": "ef5429",
                                    "textColor3": "cc7e66",
                                    "textColor4": "c14925"
                                },
                                "composerName": "alyssa michelle stephens, Dijon McFarlane, Ella Mai Howell, Shah Rukh Zaman Khan & Varren Wade",
                                "playParams": {
                                    "id": "1616728066",
                                    "kind": "song"
                                },
                                "url": "https://music.apple.com/us/album/didnt-say-feat-latto/1616728060?i=1616728066",
                                "discNumber": 1,
                                "isAppleDigitalMaster": true,
                                "hasLyrics": true,
                                "name": "Didn't Say (feat. Latto)",
                                "previews": [
                                    {
                                        "url": "https://audio-ssl.itunes.apple.com/itunes-assets/AudioPreview122/v4/65/46/30/65463007-33de-a809-4bcd-ea345c87a561/mzaf_15582090794019773151.plus.aac.p.m4a"
                                    }
                                ],
                                "artistName": "Ella Mai",
                                "contentRating": "explicit"
                            }
                        },
                        {
                            "id": "1616728067",
                            "type": "songs",
                            "href": "/v1/catalog/us/songs/1616728067",
                            "attributes": {
                                "albumName": "Heart On My Sleeve",
                                "genreNames": [
                                    "R&B/Soul",
                                    "Music"
                                ],
                                "trackNumber": 4,
                                "durationInMillis": 194826,
                                "releaseDate": "2022-05-06",
                                "isrc": "USUM72203644",
                                "artwork": {
                                    "width": 3000,
                                    "height": 3000,
                                    "url": "https://is3-ssl.mzstatic.com/image/thumb/Music112/v4/03/45/19/034519dc-9ff9-7f63-3d02-23a101a0cc3a/22UMGIM01299.rgb.jpg/{w}x{h}bb.jpg",
                                    "bgColor": "0b1b18",
                                    "textColor1": "fc977a",
                                    "textColor2": "ef5429",
                                    "textColor3": "cc7e66",
                                    "textColor4": "c14925"
                                },
                                "composerName": "Charles Hinshaw Jr, Dernst Emile II & Ella Mai Howell",
                                "playParams": {
                                    "id": "1616728067",
                                    "kind": "song"
                                },
                                "url": "https://music.apple.com/us/album/break-my-heart/1616728060?i=1616728067",
                                "discNumber": 1,
                                "hasLyrics": true,
                                "isAppleDigitalMaster": true,
                                "name": "Break My Heart",
                                "previews": [
                                    {
                                        "url": "https://audio-ssl.itunes.apple.com/itunes-assets/AudioPreview112/v4/c6/db/b2/c6dbb255-5ff5-7dcf-f2c3-4abd9cfab447/mzaf_4817315313113526902.plus.aac.p.m4a"
                                    }
                                ],
                                "artistName": "Ella Mai"
                            }
                        },
                        {
                            "id": "1616728068",
                            "type": "songs",
                            "href": "/v1/catalog/us/songs/1616728068",
                            "attributes": {
                                "albumName": "Heart On My Sleeve",
                                "genreNames": [
                                    "R&B/Soul",
                                    "Music"
                                ],
                                "trackNumber": 5,
                                "durationInMillis": 261811,
                                "releaseDate": "2022-05-06",
                                "isrc": "USUM72203646",
                                "artwork": {
                                    "width": 3000,
                                    "height": 3000,
                                    "url": "https://is3-ssl.mzstatic.com/image/thumb/Music112/v4/03/45/19/034519dc-9ff9-7f63-3d02-23a101a0cc3a/22UMGIM01299.rgb.jpg/{w}x{h}bb.jpg",
                                    "bgColor": "0b1b18",
                                    "textColor1": "fc977a",
                                    "textColor2": "ef5429",
                                    "textColor3": "cc7e66",
                                    "textColor4": "c14925"
                                },
                                "composerName": "Ari Irosogie, Ella Mai Howell, Gaeten, Jahaan Akil Sweet, Jvck James, Kirk Franklin, Marco, Richard Olowaranti Mbu Isong & Wolftyla",
                                "url": "https://music.apple.com/us/album/fallen-angel/1616728060?i=1616728068",
                                "playParams": {
                                    "id": "1616728068",
                                    "kind": "song"
                                },
                                "discNumber": 1,
                                "hasLyrics": true,
                                "isAppleDigitalMaster": true,
                                "name": "Fallen Angel",
                                "previews": [
                                    {
                                        "url": "https://audio-ssl.itunes.apple.com/itunes-assets/AudioPreview112/v4/10/09/3d/10093d6b-3371-0878-2abe-2a174be8db7c/mzaf_11447589703428563008.plus.aac.p.m4a"
                                    }
                                ],
                                "artistName": "Ella Mai"
                            }
                        },
                        {
                            "id": "1616728069",
                            "type": "songs",
                            "href": "/v1/catalog/us/songs/1616728069",
                            "attributes": {
                                "albumName": "Heart On My Sleeve",
                                "genreNames": [
                                    "R&B/Soul",
                                    "Music"
                                ],
                                "trackNumber": 6,
                                "durationInMillis": 218317,
                                "releaseDate": "2022-05-06",
                                "isrc": "USUM72203645",
                                "artwork": {
                                    "width": 3000,
                                    "height": 3000,
                                    "url": "https://is3-ssl.mzstatic.com/image/thumb/Music112/v4/03/45/19/034519dc-9ff9-7f63-3d02-23a101a0cc3a/22UMGIM01299.rgb.jpg/{w}x{h}bb.jpg",
                                    "bgColor": "0b1b18",
                                    "textColor1": "fc977a",
                                    "textColor2": "ef5429",
                                    "textColor3": "cc7e66",
                                    "textColor4": "c14925"
                                },
                                "composerName": "Bass Charity, Dijon McFarlane, Ella Mai Howell, FELICIANO ECAR, Floyd Eugene Bentley Iii, Harissis Tsakmaklis, Jorge Augusto, Luzian Tuetsch, NICHOLAS MATTHEW BALDING, Rodrick Wayne Moore & Varren Wade",
                                "playParams": {
                                    "id": "1616728069",
                                    "kind": "song"
                                },
                                "url": "https://music.apple.com/us/album/how-feat-roddy-ricch/1616728060?i=1616728069",
                                "discNumber": 1,
                                "hasLyrics": true,
                                "isAppleDigitalMaster": true,
                                "name": "How (feat. Roddy Ricch)",
                                "previews": [
                                    {
                                        "url": "https://audio-ssl.itunes.apple.com/itunes-assets/AudioPreview122/v4/d2/58/d2/d258d278-819b-3522-a1b9-2d6e8b3af57a/mzaf_8765703002683868492.plus.aac.p.m4a"
                                    }
                                ],
                                "artistName": "Ella Mai",
                                "contentRating": "explicit"
                            }
                        },
                        {
                            "id": "1616728070",
                            "type": "songs",
                            "href": "/v1/catalog/us/songs/1616728070",
                            "attributes": {
                                "albumName": "Heart On My Sleeve",
                                "genreNames": [
                                    "R&B/Soul",
                                    "Music"
                                ],
                                "trackNumber": 7,
                                "durationInMillis": 198795,
                                "releaseDate": "2022-05-06",
                                "isrc": "USUM72203650",
                                "artwork": {
                                    "width": 3000,
                                    "height": 3000,
                                    "url": "https://is3-ssl.mzstatic.com/image/thumb/Music112/v4/03/45/19/034519dc-9ff9-7f63-3d02-23a101a0cc3a/22UMGIM01299.rgb.jpg/{w}x{h}bb.jpg",
                                    "bgColor": "0b1b18",
                                    "textColor1": "fc977a",
                                    "textColor2": "ef5429",
                                    "textColor3": "cc7e66",
                                    "textColor4": "c14925"
                                },
                                "composerName": "Danny Schofield, Ella Mai Howell, Sir Nolan & Varren Wade",
                                "url": "https://music.apple.com/us/album/pieces/1616728060?i=1616728070",
                                "playParams": {
                                    "id": "1616728070",
                                    "kind": "song"
                                },
                                "discNumber": 1,
                                "hasLyrics": true,
                                "isAppleDigitalMaster": true,
                                "name": "Pieces",
                                "previews": [
                                    {
                                        "url": "https://audio-ssl.itunes.apple.com/itunes-assets/AudioPreview112/v4/25/70/e4/2570e403-e886-6663-5507-61edb075afe7/mzaf_15697244584423975937.plus.aac.p.m4a"
                                    }
                                ],
                                "artistName": "Ella Mai"
                            }
                        },
                        {
                            "id": "1616728071",
                            "type": "songs",
                            "href": "/v1/catalog/us/songs/1616728071",
                            "attributes": {
                                "albumName": "Heart On My Sleeve",
                                "genreNames": [
                                    "R&B/Soul",
                                    "Music"
                                ],
                                "trackNumber": 8,
                                "releaseDate": "2022-01-28",
                                "durationInMillis": 197517,
                                "isrc": "USUM72123679",
                                "artwork": {
                                    "width": 3000,
                                    "height": 3000,
                                    "url": "https://is3-ssl.mzstatic.com/image/thumb/Music112/v4/03/45/19/034519dc-9ff9-7f63-3d02-23a101a0cc3a/22UMGIM01299.rgb.jpg/{w}x{h}bb.jpg",
                                    "bgColor": "0b1b18",
                                    "textColor1": "fc977a",
                                    "textColor2": "ef5429",
                                    "textColor3": "cc7e66",
                                    "textColor4": "c14925"
                                },
                                "composerName": "Ella Mai Howell, Charles Hinshaw Jr, Dijon McFarlane, Daemon Landrum, Jonathan Sanders, Tyus Strickland, Donell Jones & Kyle West",
                                "playParams": {
                                    "id": "1616728071",
                                    "kind": "song"
                                },
                                "url": "https://music.apple.com/us/album/dfmu/1616728060?i=1616728071",
                                "discNumber": 1,
                                "isAppleDigitalMaster": true,
                                "hasLyrics": true,
                                "name": "DFMU",
                                "previews": [
                                    {
                                        "url": "https://audio-ssl.itunes.apple.com/itunes-assets/AudioPreview112/v4/87/2b/a2/872ba250-ba86-aadc-e97e-bf840f9956cf/mzaf_5160210617366591062.plus.aac.p.m4a"
                                    }
                                ],
                                "artistName": "Ella Mai",
                                "contentRating": "explicit"
                            }
                        },
                        {
                            "id": "1616728074",
                            "type": "songs",
                            "href": "/v1/catalog/us/songs/1616728074",
                            "attributes": {
                                "albumName": "Heart On My Sleeve",
                                "genreNames": [
                                    "R&B/Soul",
                                    "Music"
                                ],
                                "trackNumber": 9,
                                "durationInMillis": 208119,
                                "releaseDate": "2022-05-06",
                                "isrc": "USUM72203649",
                                "artwork": {
                                    "width": 3000,
                                    "height": 3000,
                                    "url": "https://is3-ssl.mzstatic.com/image/thumb/Music112/v4/03/45/19/034519dc-9ff9-7f63-3d02-23a101a0cc3a/22UMGIM01299.rgb.jpg/{w}x{h}bb.jpg",
                                    "bgColor": "0b1b18",
                                    "textColor1": "fc977a",
                                    "textColor2": "ef5429",
                                    "textColor3": "cc7e66",
                                    "textColor4": "c14925"
                                },
                                "composerName": "Charles Hinshaw Jr, Dijon McFarlane, Ella Mai Howell & Wolftyla",
                                "playParams": {
                                    "id": "1616728074",
                                    "kind": "song"
                                },
                                "url": "https://music.apple.com/us/album/hide/1616728060?i=1616728074",
                                "discNumber": 1,
                                "hasLyrics": true,
                                "isAppleDigitalMaster": true,
                                "name": "Hide",
                                "previews": [
                                    {
                                        "url": "https://audio-ssl.itunes.apple.com/itunes-assets/AudioPreview122/v4/3f/f2/50/3ff25066-b511-e1f9-a035-7bc2f554117a/mzaf_5200904665505669763.plus.aac.p.m4a"
                                    }
                                ],
                                "artistName": "Ella Mai"
                            }
                        },
                        {
                            "id": "1616728075",
                            "type": "songs",
                            "href": "/v1/catalog/us/songs/1616728075",
                            "attributes": {
                                "albumName": "Heart On My Sleeve",
                                "genreNames": [
                                    "R&B/Soul",
                                    "Music"
                                ],
                                "trackNumber": 10,
                                "releaseDate": "2022-05-06",
                                "durationInMillis": 213885,
                                "isrc": "USUM72203652",
                                "artwork": {
                                    "width": 3000,
                                    "height": 3000,
                                    "url": "https://is3-ssl.mzstatic.com/image/thumb/Music112/v4/03/45/19/034519dc-9ff9-7f63-3d02-23a101a0cc3a/22UMGIM01299.rgb.jpg/{w}x{h}bb.jpg",
                                    "bgColor": "0b1b18",
                                    "textColor1": "fc977a",
                                    "textColor2": "ef5429",
                                    "textColor3": "cc7e66",
                                    "textColor4": "c14925"
                                },
                                "composerName": "Cam Griffin, Dijon McFarlane, Ella Mai Howell, Jason Pounds & Varren Wade",
                                "url": "https://music.apple.com/us/album/power-of-a-woman/1616728060?i=1616728075",
                                "playParams": {
                                    "id": "1616728075",
                                    "kind": "song"
                                },
                                "discNumber": 1,
                                "isAppleDigitalMaster": true,
                                "hasLyrics": true,
                                "name": "Power Of A Woman",
                                "previews": [
                                    {
                                        "url": "https://audio-ssl.itunes.apple.com/itunes-assets/AudioPreview122/v4/4c/2e/49/4c2e49d8-4cbe-7fb1-1d06-43e601b096a8/mzaf_1661246820128533834.plus.aac.p.m4a"
                                    }
                                ],
                                "artistName": "Ella Mai"
                            }
                        },
                        {
                            "id": "1616728080",
                            "type": "songs",
                            "href": "/v1/catalog/us/songs/1616728080",
                            "attributes": {
                                "albumName": "Heart On My Sleeve",
                                "genreNames": [
                                    "R&B/Soul",
                                    "Music"
                                ],
                                "trackNumber": 11,
                                "durationInMillis": 233794,
                                "releaseDate": "2022-05-06",
                                "isrc": "USUM72203640",
                                "artwork": {
                                    "width": 3000,
                                    "height": 3000,
                                    "url": "https://is3-ssl.mzstatic.com/image/thumb/Music112/v4/03/45/19/034519dc-9ff9-7f63-3d02-23a101a0cc3a/22UMGIM01299.rgb.jpg/{w}x{h}bb.jpg",
                                    "bgColor": "0b1b18",
                                    "textColor1": "fc977a",
                                    "textColor2": "ef5429",
                                    "textColor3": "cc7e66",
                                    "textColor4": "c14925"
                                },
                                "composerName": "Cameron Joseph, David Brown, Ella Mai Howell, Matthew Samuels, Michael Samuels Jr., Mike McGregor & Peter Iskander",
                                "url": "https://music.apple.com/us/album/a-mess-feat-lucky-daye/1616728060?i=1616728080",
                                "playParams": {
                                    "id": "1616728080",
                                    "kind": "song"
                                },
                                "discNumber": 1,
                                "hasLyrics": true,
                                "isAppleDigitalMaster": true,
                                "name": "A Mess (feat. Lucky Daye)",
                                "previews": [
                                    {
                                        "url": "https://audio-ssl.itunes.apple.com/itunes-assets/AudioPreview112/v4/d4/65/93/d46593a6-4b74-d40a-a5c9-1ff0e836e5d4/mzaf_15047800783622526169.plus.aac.p.m4a"
                                    }
                                ],
                                "contentRating": "explicit",
                                "artistName": "Ella Mai"
                            }
                        },
                        {
                            "id": "1616728297",
                            "type": "songs",
                            "href": "/v1/catalog/us/songs/1616728297",
                            "attributes": {
                                "albumName": "Heart On My Sleeve",
                                "genreNames": [
                                    "R&B/Soul",
                                    "Music"
                                ],
                                "trackNumber": 12,
                                "releaseDate": "2022-05-06",
                                "durationInMillis": 199909,
                                "isrc": "USUM72203648",
                                "artwork": {
                                    "width": 3000,
                                    "height": 3000,
                                    "url": "https://is3-ssl.mzstatic.com/image/thumb/Music112/v4/03/45/19/034519dc-9ff9-7f63-3d02-23a101a0cc3a/22UMGIM01299.rgb.jpg/{w}x{h}bb.jpg",
                                    "bgColor": "0b1b18",
                                    "textColor1": "fc977a",
                                    "textColor2": "ef5429",
                                    "textColor3": "cc7e66",
                                    "textColor4": "c14925"
                                },
                                "composerName": "Chloe George, Ella Mai Howell, Jorgen Odegard & Stephanie Nicole Jones",
                                "url": "https://music.apple.com/us/album/feels-like/1616728060?i=1616728297",
                                "playParams": {
                                    "id": "1616728297",
                                    "kind": "song"
                                },
                                "discNumber": 1,
                                "isAppleDigitalMaster": true,
                                "hasLyrics": true,
                                "name": "Feels Like",
                                "previews": [
                                    {
                                        "url": "https://audio-ssl.itunes.apple.com/itunes-assets/AudioPreview112/v4/f6/4d/74/f64d7407-86f1-d037-6b87-014128226145/mzaf_12176941177166656131.plus.aac.p.m4a"
                                    }
                                ],
                                "artistName": "Ella Mai",
                                "contentRating": "explicit"
                            }
                        },
                        {
                            "id": "1616728300",
                            "type": "songs",
                            "href": "/v1/catalog/us/songs/1616728300",
                            "attributes": {
                                "albumName": "Heart On My Sleeve",
                                "genreNames": [
                                    "R&B/Soul",
                                    "Music"
                                ],
                                "trackNumber": 13,
                                "releaseDate": "2022-04-02",
                                "durationInMillis": 209136,
                                "isrc": "USUM72203641",
                                "artwork": {
                                    "width": 3000,
                                    "height": 3000,
                                    "url": "https://is3-ssl.mzstatic.com/image/thumb/Music112/v4/03/45/19/034519dc-9ff9-7f63-3d02-23a101a0cc3a/22UMGIM01299.rgb.jpg/{w}x{h}bb.jpg",
                                    "bgColor": "0b1b18",
                                    "textColor1": "fc977a",
                                    "textColor2": "ef5429",
                                    "textColor3": "cc7e66",
                                    "textColor4": "c14925"
                                },
                                "composerName": "Ella Mai Howell, Varren Wade, Harmony Samuels & Edgar Etienne",
                                "playParams": {
                                    "id": "1616728300",
                                    "kind": "song"
                                },
                                "url": "https://music.apple.com/us/album/leave-you-alone/1616728060?i=1616728300",
                                "discNumber": 1,
                                "isAppleDigitalMaster": true,
                                "hasLyrics": true,
                                "name": "Leave You Alone",
                                "previews": [
                                    {
                                        "url": "https://audio-ssl.itunes.apple.com/itunes-assets/AudioPreview122/v4/4e/99/03/4e9903bc-c099-2b91-f725-5f4034930e55/mzaf_12018132630264518586.plus.aac.p.m4a"
                                    }
                                ],
                                "artistName": "Ella Mai",
                                "contentRating": "explicit"
                            }
                        },
                        {
                            "id": "1616728301",
                            "type": "songs",
                            "href": "/v1/catalog/us/songs/1616728301",
                            "attributes": {
                                "albumName": "Heart On My Sleeve",
                                "genreNames": [
                                    "R&B/Soul",
                                    "Music"
                                ],
                                "trackNumber": 14,
                                "durationInMillis": 234613,
                                "releaseDate": "2022-05-06",
                                "isrc": "USUM72203651",
                                "artwork": {
                                    "width": 3000,
                                    "height": 3000,
                                    "url": "https://is3-ssl.mzstatic.com/image/thumb/Music112/v4/03/45/19/034519dc-9ff9-7f63-3d02-23a101a0cc3a/22UMGIM01299.rgb.jpg/{w}x{h}bb.jpg",
                                    "bgColor": "0b1b18",
                                    "textColor1": "fc977a",
                                    "textColor2": "ef5429",
                                    "textColor3": "cc7e66",
                                    "textColor4": "c14925"
                                },
                                "composerName": "Charles Hinshaw Jr, Dernst Emile II, Ella Mai Howell & Mary J. Blige",
                                "playParams": {
                                    "id": "1616728301",
                                    "kind": "song"
                                },
                                "url": "https://music.apple.com/us/album/sink-or-swim/1616728060?i=1616728301",
                                "discNumber": 1,
                                "hasLyrics": true,
                                "isAppleDigitalMaster": true,
                                "name": "Sink or Swim",
                                "previews": [
                                    {
                                        "url": "https://audio-ssl.itunes.apple.com/itunes-assets/AudioPreview122/v4/85/63/1d/85631d29-7bc9-5815-5f32-b8fa02789d23/mzaf_2125550395281668690.plus.aac.p.m4a"
                                    }
                                ],
                                "artistName": "Ella Mai",
                                "contentRating": "explicit"
                            }
                        },
                        {
                            "id": "1616728302",
                            "type": "songs",
                            "href": "/v1/catalog/us/songs/1616728302",
                            "attributes": {
                                "albumName": "Heart On My Sleeve",
                                "genreNames": [
                                    "R&B/Soul",
                                    "Music"
                                ],
                                "trackNumber": 15,
                                "releaseDate": "2022-05-06",
                                "durationInMillis": 214882,
                                "isrc": "USUM72203639",
                                "artwork": {
                                    "width": 3000,
                                    "height": 3000,
                                    "url": "https://is3-ssl.mzstatic.com/image/thumb/Music112/v4/03/45/19/034519dc-9ff9-7f63-3d02-23a101a0cc3a/22UMGIM01299.rgb.jpg/{w}x{h}bb.jpg",
                                    "bgColor": "0b1b18",
                                    "textColor1": "fc977a",
                                    "textColor2": "ef5429",
                                    "textColor3": "cc7e66",
                                    "textColor4": "c14925"
                                },
                                "composerName": "Ella Mai Howell, Jahaan Akil Sweet & Varren Wade",
                                "url": "https://music.apple.com/us/album/fading-out/1616728060?i=1616728302",
                                "playParams": {
                                    "id": "1616728302",
                                    "kind": "song"
                                },
                                "discNumber": 1,
                                "isAppleDigitalMaster": true,
                                "hasLyrics": true,
                                "name": "Fading Out",
                                "previews": [
                                    {
                                        "url": "https://audio-ssl.itunes.apple.com/itunes-assets/AudioPreview122/v4/1d/23/8f/1d238f3b-f1d0-ef0a-aec6-a1cfda070e6c/mzaf_16442520982162034651.plus.aac.p.m4a"
                                    }
                                ],
                                "artistName": "Ella Mai",
                                "contentRating": "explicit"
                            }
                        }
                    ]
                }
            }
        }
    ]
}

```

## See Also

### Related Documentation

object Albums

A resource object that represents an album.

object AlbumsResponse

The response to an albums request.

### Requesting Catalog Albums

Get a Catalog Album's Relationship Directly by Name

Fetch an album’s relationship by using its identifier.

Get a Catalog Album’s Relationship View Directly by Name

Fetch related resources for a single album’s relationship view.

Get Multiple Catalog Albums

Fetch one or more albums by using their identifiers.

Get Multiple Catalog Albums by UPC

Fetch one or more albums by using their UPC values.

Get Equivalent Catalog Albums by ID

Fetch the equivalent, available content in the storefront for the provided albums’ identifiers.

