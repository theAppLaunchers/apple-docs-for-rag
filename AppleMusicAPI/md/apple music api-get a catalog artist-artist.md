

- Apple Music API
-  Get a Catalog Artist 

Web Service Endpoint

# Get a Catalog Artist

Fetch an artist by using the artist’s identifier.

Apple Music 1.0+

## URL

``` source
GET https://api.music.apple.com/v1/catalog/{storefront}/artists/{id}
```

## Path Parameters

`id`

`string`

 (Required) 

The unique identifier for the artist.

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

Possible Values: `appears-on-albums, compilation-albums, featured-albums, featured-music-videos, featured-playlists, full-albums, latest-release, live-albums, similar-artists, singles, top-music-videos, top-songs`

`extend`

`[string]`

A list of attribute extensions to apply to resources in the response.

## Response Codes

` 200 ``OK`

ArtistsResponse

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
https://api.music.apple.com/v1/catalog/us/artists/1147783278
```

```
{
    "data": [
        {
            "id": "1147783278",
            "type": "artists",
            "href": "/v1/catalog/us/artists/1147783278",
            "attributes": {
                "genreNames": [
                    "Alternative"
                ],
                "name": "Beach Bunny",
                "artwork": {
                    "width": 2011,
                    "height": 2011,
                    "url": "https://is4-ssl.mzstatic.com/image/thumb/Music122/v4/ee/38/80/ee3880eb-e996-8b35-887f-c71c8ad800ac/pr_source.png/{w}x{h}bb.jpg",
                    "bgColor": "19160f",
                    "textColor1": "f3949b",
                    "textColor2": "b08ff2",
                    "textColor3": "c77b7f",
                    "textColor4": "9277c5"
                },
                "url": "https://music.apple.com/us/artist/beach-bunny/1147783278"
            },
            "relationships": {
                "albums": {
                    "href": "/v1/catalog/us/artists/1147783278/albums",
                    "data": [
                        {
                            "id": "1482041821",
                            "type": "albums",
                            "href": "/v1/catalog/us/albums/1482041821"
                        },
                        {
                            "id": "1613600183",
                            "type": "albums",
                            "href": "/v1/catalog/us/albums/1613600183"
                        },
                        {
                            "id": "1476463573",
                            "type": "albums",
                            "href": "/v1/catalog/us/albums/1476463573"
                        },
                        {
                            "id": "1476463541",
                            "type": "albums",
                            "href": "/v1/catalog/us/albums/1476463541"
                        },
                        {
                            "id": "1537898980",
                            "type": "albums",
                            "href": "/v1/catalog/us/albums/1537898980"
                        },
                        {
                            "id": "1147798746",
                            "type": "albums",
                            "href": "/v1/catalog/us/albums/1147798746"
                        },
                        {
                            "id": "1147782780",
                            "type": "albums",
                            "href": "/v1/catalog/us/albums/1147782780"
                        },
                        {
                            "id": "1445627459",
                            "type": "albums",
                            "href": "/v1/catalog/us/albums/1445627459"
                        },
                        {
                            "id": "1589473324",
                            "type": "albums",
                            "href": "/v1/catalog/us/albums/1589473324"
                        },
                        {
                            "id": "1509311498",
                            "type": "albums",
                            "href": "/v1/catalog/us/albums/1509311498"
                        },
                        {
                            "id": "1562419539",
                            "type": "albums",
                            "href": "/v1/catalog/us/albums/1562419539"
                        },
                        {
                            "id": "1243697430",
                            "type": "albums",
                            "href": "/v1/catalog/us/albums/1243697430"
                        },
                        {
                            "id": "1590556925",
                            "type": "albums",
                            "href": "/v1/catalog/us/albums/1590556925"
                        },
                        {
                            "id": "1596358408",
                            "type": "albums",
                            "href": "/v1/catalog/us/albums/1596358408"
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

object Artists

A resource object that represents the artist of an album where an artist can be one or more people.

object ArtistsResponse

The response to an artists request.

### Requesting a Catalog Artist

Get a Catalog Artist's Relationship Directly by Name

Fetch an artist’s relationship by using its identifier.

Get a Catalog Artist’s Relationship View Directly by Name

Fetch related resources for a single artist’s relationship view.

Get Multiple Catalog Artists

Fetch one or more artists by using their identifiers.

