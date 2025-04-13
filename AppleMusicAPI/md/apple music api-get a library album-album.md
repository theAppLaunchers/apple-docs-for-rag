

- Apple Music API
-  Get a Library Album 

Web Service Endpoint

# Get a Library Album

Fetch a library album by using its identifier.

Apple Music 1.0+

## URL

``` source
GET https://api.music.apple.com/v1/me/library/albums/{id}
```

## Path Parameters

`id`

`string`

 (Required) 

The unique identifier for the album.

## Query Parameters

`l`

`string`

The localization to use, specified by a language tag. The possible values are in the `supportedLanguageTags` array belonging to the `Storefront` object specified by `storefront`. Otherwise, the default is `defaultLanguageTag` in `Storefront`.

`include`

`[string]`

Additional relationships to include in the fetch.

`extend`

`[string]`

A list of attribute extensions to apply to resources in the response.

## Response Codes

` 200 ``OK`

LibraryAlbumsResponse

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

If successful, the HTTP status code is 200 (OK) and the `data` array contains the requested resource object. If unsuccessful, the HTTP status code indicates the error and the details are in the `errors` array.

This endpoint requires a music user token. For more information, see User Authentication for MusicKit.

### Example

- Request
- Response

```
https://api.music.apple.com/v1/me/library/albums/l.sticiFl
```

```
{    
     "data": [
        {
            "id": "l.sticiFl",
            "type": "library-albums",
            "href": "/v1/me/library/albums/l.sticiFl",
            "attributes": {
                "trackCount": 15,
                "genreNames": [
                    "Country"
                ],
                "releaseDate": "2022-02-11",
                "name": "Bronco",
                "artistName": "Orville Peck",
                "artwork": {
                    "width": 1200,
                    "height": 1200,
                    "url": "https://is3-ssl.mzstatic.com/image/thumb/Music116/v4/6d/de/02/6dde02ae-a9fe-f96e-e81f-4f18ad13d2f9/886449873302.jpg/{w}x{h}bb.jpg"
                },
                "playParams": {
                    "id": "l.sticiFl",
                    "kind": "album",
                    "isLibrary": true
                },
                "dateAdded": "2022-08-06T02:18:57Z"
            },
            "relationships": {
                "tracks": {
                    "href": "/v1/me/library/albums/l.sticiFl/tracks",
                    "data": [
                        {
                            "id": "i.PkdJJamIrQozOW",
                            "type": "library-songs",
                            "href": "/v1/me/library/songs/i.PkdJJamIrQozOW",
                            "attributes": {
                                "discNumber": 1,
                                "albumName": "Bronco",
                                "genreNames": [
                                    "Country"
                                ],
                                "trackNumber": 1,
                                "hasLyrics": true,
                                "durationInMillis": 195160,
                                "releaseDate": "2022-02-11",
                                "name": "Daytona Sand",
                                "artistName": "Orville Peck",
                                "artwork": {
                                    "width": 1200,
                                    "height": 1200,
                                    "url": "https://is3-ssl.mzstatic.com/image/thumb/Music116/v4/6d/de/02/6dde02ae-a9fe-f96e-e81f-4f18ad13d2f9/886449873302.jpg/{w}x{h}bb.jpg"
                                },
                                "playParams": {
                                    "id": "i.PkdJJamIrQozOW",
                                    "kind": "song",
                                    "isLibrary": true,
                                    "reporting": true,
                                    "catalogId": "1607593874",
                                    "reportingId": "1607593874"
                                }
                            }
                        },
                        {
                            "id": "i.6xpKRzXt6rDz0g",
                            "type": "library-songs",
                            "href": "/v1/me/library/songs/i.6xpKRzXt6rDz0g",
                            "attributes": {
                                "albumName": "Bronco",
                                "discNumber": 1,
                                "genreNames": [
                                    "Country"
                                ],
                                "trackNumber": 2,
                                "hasLyrics": true,
                                "releaseDate": "2022-03-11",
                                "durationInMillis": 250213,
                                "name": "The Curse of the Blackened Eye",
                                "artistName": "Orville Peck",
                                "artwork": {
                                    "width": 1200,
                                    "height": 1200,
                                    "url": "https://is3-ssl.mzstatic.com/image/thumb/Music116/v4/6d/de/02/6dde02ae-a9fe-f96e-e81f-4f18ad13d2f9/886449873302.jpg/{w}x{h}bb.jpg"
                                },
                                "playParams": {
                                    "id": "i.6xpKRzXt6rDz0g",
                                    "kind": "song",
                                    "isLibrary": true,
                                    "reporting": true,
                                    "catalogId": "1607593881",
                                    "reportingId": "1607593881"
                                }
                            }
                        },
                        {
                            "id": "i.ZOM0NoJiAelKXG",
                            "type": "library-songs",
                            "href": "/v1/me/library/songs/i.ZOM0NoJiAelKXG",
                            "attributes": {
                                "albumName": "Bronco",
                                "discNumber": 1,
                                "genreNames": [
                                    "Country"
                                ],
                                "trackNumber": 3,
                                "hasLyrics": true,
                                "releaseDate": "2022-02-11",
                                "durationInMillis": 258667,
                                "name": "Outta Time",
                                "artistName": "Orville Peck",
                                "artwork": {
                                    "width": 1200,
                                    "height": 1200,
                                    "url": "https://is3-ssl.mzstatic.com/image/thumb/Music116/v4/6d/de/02/6dde02ae-a9fe-f96e-e81f-4f18ad13d2f9/886449873302.jpg/{w}x{h}bb.jpg"
                                },
                                "playParams": {
                                    "id": "i.ZOM0NoJiAelKXG",
                                    "kind": "song",
                                    "isLibrary": true,
                                    "reporting": true,
                                    "catalogId": "1607593891",
                                    "reportingId": "1607593891"
                                }
                            }
                        },
                        {
                            "id": "i.1YBmxKOcWM0k5b",
                            "type": "library-songs",
                            "href": "/v1/me/library/songs/i.1YBmxKOcWM0k5b",
                            "attributes": {
                                "discNumber": 1,
                                "albumName": "Bronco",
                                "genreNames": [
                                    "Country"
                                ],
                                "hasLyrics": true,
                                "trackNumber": 4,
                                "durationInMillis": 182000,
                                "releaseDate": "2022-04-08",
                                "name": "Lafayette",
                                "artistName": "Orville Peck",
                                "artwork": {
                                    "width": 1200,
                                    "height": 1200,
                                    "url": "https://is3-ssl.mzstatic.com/image/thumb/Music116/v4/6d/de/02/6dde02ae-a9fe-f96e-e81f-4f18ad13d2f9/886449873302.jpg/{w}x{h}bb.jpg"
                                },
                                "playParams": {
                                    "id": "i.1YBmxKOcWM0k5b",
                                    "kind": "song",
                                    "isLibrary": true,
                                    "reporting": true,
                                    "catalogId": "1607593893",
                                    "reportingId": "1607593893"
                                }
                            }
                        },
                        {
                            "id": "i.V7Ba9oJh2E8okV",
                            "type": "library-songs",
                            "href": "/v1/me/library/songs/i.V7Ba9oJh2E8okV",
                            "attributes": {
                                "discNumber": 1,
                                "albumName": "Bronco",
                                "genreNames": [
                                    "Country"
                                ],
                                "hasLyrics": true,
                                "trackNumber": 5,
                                "durationInMillis": 210840,
                                "releaseDate": "2022-02-11",
                                "name": "C'mon Baby, Cry",
                                "artistName": "Orville Peck",
                                "artwork": {
                                    "width": 1200,
                                    "height": 1200,
                                    "url": "https://is3-ssl.mzstatic.com/image/thumb/Music116/v4/6d/de/02/6dde02ae-a9fe-f96e-e81f-4f18ad13d2f9/886449873302.jpg/{w}x{h}bb.jpg"
                                },
                                "playParams": {
                                    "id": "i.V7Ba9oJh2E8okV",
                                    "kind": "song",
                                    "isLibrary": true,
                                    "reporting": true,
                                    "catalogId": "1607593895",
                                    "reportingId": "1607593895"
                                }
                            }
                        },
                        {
                            "id": "i.AWPVEmkhDE7rz8",
                            "type": "library-songs",
                            "href": "/v1/me/library/songs/i.AWPVEmkhDE7rz8",
                            "attributes": {
                                "albumName": "Bronco",
                                "discNumber": 1,
                                "genreNames": [
                                    "Country"
                                ],
                                "trackNumber": 6,
                                "hasLyrics": true,
                                "releaseDate": "2022-04-08",
                                "durationInMillis": 168587,
                                "name": "Iris Rose",
                                "artistName": "Orville Peck",
                                "artwork": {
                                    "width": 1200,
                                    "height": 1200,
                                    "url": "https://is3-ssl.mzstatic.com/image/thumb/Music116/v4/6d/de/02/6dde02ae-a9fe-f96e-e81f-4f18ad13d2f9/886449873302.jpg/{w}x{h}bb.jpg"
                                },
                                "playParams": {
                                    "id": "i.AWPVEmkhDE7rz8",
                                    "kind": "song",
                                    "isLibrary": true,
                                    "reporting": true,
                                    "catalogId": "1607593958",
                                    "reportingId": "1607593958"
                                }
                            }
                        },
                        {
                            "id": "i.V7Ba9oPs2E8okV",
                            "type": "library-songs",
                            "href": "/v1/me/library/songs/i.V7Ba9oPs2E8okV",
                            "attributes": {
                                "albumName": "Bronco",
                                "discNumber": 1,
                                "genreNames": [
                                    "Country"
                                ],
                                "trackNumber": 7,
                                "hasLyrics": true,
                                "releaseDate": "2022-03-11",
                                "durationInMillis": 289587,
                                "name": "Kalahari Down",
                                "artistName": "Orville Peck",
                                "artwork": {
                                    "width": 1200,
                                    "height": 1200,
                                    "url": "https://is3-ssl.mzstatic.com/image/thumb/Music116/v4/6d/de/02/6dde02ae-a9fe-f96e-e81f-4f18ad13d2f9/886449873302.jpg/{w}x{h}bb.jpg"
                                },
                                "playParams": {
                                    "id": "i.V7Ba9oPs2E8okV",
                                    "kind": "song",
                                    "isLibrary": true,
                                    "reporting": true,
                                    "catalogId": "1607593960",
                                    "reportingId": "1607593960"
                                }
                            }
                        },
                        {
                            "id": "i.O1RQpZrsG2RmWD",
                            "type": "library-songs",
                            "href": "/v1/me/library/songs/i.O1RQpZrsG2RmWD",
                            "attributes": {
                                "discNumber": 1,
                                "albumName": "Bronco",
                                "genreNames": [
                                    "Country"
                                ],
                                "hasLyrics": true,
                                "trackNumber": 8,
                                "durationInMillis": 208893,
                                "releaseDate": "2022-04-08",
                                "name": "Bronco",
                                "artistName": "Orville Peck",
                                "artwork": {
                                    "width": 1200,
                                    "height": 1200,
                                    "url": "https://is3-ssl.mzstatic.com/image/thumb/Music116/v4/6d/de/02/6dde02ae-a9fe-f96e-e81f-4f18ad13d2f9/886449873302.jpg/{w}x{h}bb.jpg"
                                },
                                "playParams": {
                                    "id": "i.O1RQpZrsG2RmWD",
                                    "kind": "song",
                                    "isLibrary": true,
                                    "reporting": true,
                                    "catalogId": "1607593961",
                                    "reportingId": "1607593961"
                                }
                            }
                        },
                        {
                            "id": "i.O1RQpZGuG2RmWD",
                            "type": "library-songs",
                            "href": "/v1/me/library/songs/i.O1RQpZGuG2RmWD",
                            "attributes": {
                                "discNumber": 1,
                                "albumName": "Bronco",
                                "genreNames": [
                                    "Country"
                                ],
                                "trackNumber": 9,
                                "hasLyrics": true,
                                "durationInMillis": 228160,
                                "releaseDate": "2022-04-08",
                                "name": "Trample Out the Days",
                                "artistName": "Orville Peck",
                                "artwork": {
                                    "width": 1200,
                                    "height": 1200,
                                    "url": "https://is3-ssl.mzstatic.com/image/thumb/Music116/v4/6d/de/02/6dde02ae-a9fe-f96e-e81f-4f18ad13d2f9/886449873302.jpg/{w}x{h}bb.jpg"
                                },
                                "playParams": {
                                    "id": "i.O1RQpZGuG2RmWD",
                                    "kind": "song",
                                    "isLibrary": true,
                                    "reporting": true,
                                    "catalogId": "1607593962",
                                    "reportingId": "1607593962"
                                }
                            }
                        },
                        {
                            "id": "i.AWPVEm0sDE7rz8",
                            "type": "library-songs",
                            "href": "/v1/me/library/songs/i.AWPVEm0sDE7rz8",
                            "attributes": {
                                "discNumber": 1,
                                "albumName": "Bronco",
                                "genreNames": [
                                    "Country"
                                ],
                                "hasLyrics": true,
                                "trackNumber": 10,
                                "durationInMillis": 216907,
                                "releaseDate": "2022-04-08",
                                "name": "Blush",
                                "artistName": "Orville Peck",
                                "artwork": {
                                    "width": 1200,
                                    "height": 1200,
                                    "url": "https://is3-ssl.mzstatic.com/image/thumb/Music116/v4/6d/de/02/6dde02ae-a9fe-f96e-e81f-4f18ad13d2f9/886449873302.jpg/{w}x{h}bb.jpg"
                                },
                                "playParams": {
                                    "id": "i.AWPVEm0sDE7rz8",
                                    "kind": "song",
                                    "isLibrary": true,
                                    "reporting": true,
                                    "catalogId": "1607593963",
                                    "reportingId": "1607593963"
                                }
                            }
                        },
                        {
                            "id": "i.qQd8aY0U1vV7Ma",
                            "type": "library-songs",
                            "href": "/v1/me/library/songs/i.qQd8aY0U1vV7Ma",
                            "attributes": {
                                "discNumber": 1,
                                "albumName": "Bronco",
                                "genreNames": [
                                    "Country"
                                ],
                                "hasLyrics": true,
                                "trackNumber": 11,
                                "durationInMillis": 191920,
                                "releaseDate": "2022-03-11",
                                "name": "Hexie Mountains",
                                "artistName": "Orville Peck",
                                "artwork": {
                                    "width": 1200,
                                    "height": 1200,
                                    "url": "https://is3-ssl.mzstatic.com/image/thumb/Music116/v4/6d/de/02/6dde02ae-a9fe-f96e-e81f-4f18ad13d2f9/886449873302.jpg/{w}x{h}bb.jpg"
                                },
                                "playParams": {
                                    "id": "i.qQd8aY0U1vV7Ma",
                                    "kind": "song",
                                    "isLibrary": true,
                                    "reporting": true,
                                    "catalogId": "1607593965",
                                    "reportingId": "1607593965"
                                }
                            }
                        },
                        {
                            "id": "i.gelXNbYFMg4aPB",
                            "type": "library-songs",
                            "href": "/v1/me/library/songs/i.gelXNbYFMg4aPB",
                            "attributes": {
                                "discNumber": 1,
                                "albumName": "Bronco",
                                "genreNames": [
                                    "Country"
                                ],
                                "hasLyrics": true,
                                "trackNumber": 12,
                                "durationInMillis": 199653,
                                "releaseDate": "2022-04-08",
                                "name": "Let Me Drown",
                                "artistName": "Orville Peck",
                                "artwork": {
                                    "width": 1200,
                                    "height": 1200,
                                    "url": "https://is3-ssl.mzstatic.com/image/thumb/Music116/v4/6d/de/02/6dde02ae-a9fe-f96e-e81f-4f18ad13d2f9/886449873302.jpg/{w}x{h}bb.jpg"
                                },
                                "playParams": {
                                    "id": "i.gelXNbYFMg4aPB",
                                    "kind": "song",
                                    "isLibrary": true,
                                    "reporting": true,
                                    "catalogId": "1607593967",
                                    "reportingId": "1607593967"
                                }
                            }
                        },
                        {
                            "id": "i.gelXXYohMg4aPB",
                            "type": "library-songs",
                            "href": "/v1/me/library/songs/i.gelXXYohMg4aPB",
                            "attributes": {
                                "discNumber": 1,
                                "albumName": "Bronco",
                                "genreNames": [
                                    "Country"
                                ],
                                "hasLyrics": true,
                                "trackNumber": 13,
                                "durationInMillis": 136000,
                                "releaseDate": "2022-02-11",
                                "name": "Any Turn",
                                "artistName": "Orville Peck",
                                "artwork": {
                                    "width": 1200,
                                    "height": 1200,
                                    "url": "https://is3-ssl.mzstatic.com/image/thumb/Music116/v4/6d/de/02/6dde02ae-a9fe-f96e-e81f-4f18ad13d2f9/886449873302.jpg/{w}x{h}bb.jpg"
                                },
                                "playParams": {
                                    "id": "i.gelXXYohMg4aPB",
                                    "kind": "song",
                                    "isLibrary": true,
                                    "reporting": true,
                                    "catalogId": "1607593968",
                                    "reportingId": "1607593968"
                                }
                            }
                        },
                        {
                            "id": "i.LVk44LYU2bV0qR",
                            "type": "library-songs",
                            "href": "/v1/me/library/songs/i.LVk44LYU2bV0qR",
                            "attributes": {
                                "discNumber": 1,
                                "albumName": "Bronco",
                                "genreNames": [
                                    "Country"
                                ],
                                "trackNumber": 14,
                                "hasLyrics": true,
                                "durationInMillis": 244093,
                                "releaseDate": "2022-04-08",
                                "name": "City of Gold",
                                "artistName": "Orville Peck",
                                "artwork": {
                                    "width": 1200,
                                    "height": 1200,
                                    "url": "https://is3-ssl.mzstatic.com/image/thumb/Music116/v4/6d/de/02/6dde02ae-a9fe-f96e-e81f-4f18ad13d2f9/886449873302.jpg/{w}x{h}bb.jpg"
                                },
                                "playParams": {
                                    "id": "i.LVk44LYU2bV0qR",
                                    "kind": "song",
                                    "isLibrary": true,
                                    "reporting": true,
                                    "catalogId": "1607593970",
                                    "reportingId": "1607593970"
                                }
                            }
                        },
                        {
                            "id": "i.QvzgNpeFEBxbzJ",
                            "type": "library-songs",
                            "href": "/v1/me/library/songs/i.QvzgNpeFEBxbzJ",
                            "attributes": {
                                "discNumber": 1,
                                "albumName": "Bronco",
                                "genreNames": [
                                    "Country"
                                ],
                                "hasLyrics": true,
                                "trackNumber": 15,
                                "durationInMillis": 236360,
                                "releaseDate": "2022-04-08",
                                "name": "All I Can Say",
                                "artistName": "Orville Peck",
                                "artwork": {
                                    "width": 1200,
                                    "height": 1200,
                                    "url": "https://is3-ssl.mzstatic.com/image/thumb/Music116/v4/6d/de/02/6dde02ae-a9fe-f96e-e81f-4f18ad13d2f9/886449873302.jpg/{w}x{h}bb.jpg"
                                },
                                "playParams": {
                                    "id": "i.QvzgNpeFEBxbzJ",
                                    "kind": "song",
                                    "isLibrary": true,
                                    "reporting": true,
                                    "catalogId": "1607593972",
                                    "reportingId": "1607593972"
                                }
                            }
                        }
                    ],
                    "meta": {
                        "total": 15
                    }
                }
            }
        }
    ]
}

```

## See Also

### Related Documentation

object LibraryAlbums

A resource object that represents a library album.

object LibraryAlbumsResponse

The response to a library albums request.

### Requesting User Library Albums

Get a Library Album's Relationship Directly by Name

Fetch a library album’s relationship by using its identifier.

Get Multiple Library Albums

Fetch one or more library albums by using their identifiers.

Get All Library Albums

Fetch all the library albums in alphabetical order.

