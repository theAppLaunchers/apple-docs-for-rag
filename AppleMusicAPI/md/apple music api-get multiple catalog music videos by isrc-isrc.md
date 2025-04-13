

- Apple Music API
-  Get Multiple Catalog Music Videos by ISRC 

Web Service Endpoint

# Get Multiple Catalog Music Videos by ISRC

Fetch one or more music videos by using their International Standard Recording Code (ISRC) values.

Apple Music 1.0+

## URL

``` source
GET https://api.music.apple.com/v1/catalog/{storefront}/music-videos
```

## Path Parameters

`storefront`

`string`

 (Required) 

An iTunes Store territory, specified by an ISO 3166 alpha-2 country code. The possible values are the `id` attributes of `Storefront` objects.

## Query Parameters

`filter[isrc]`

`[string]`

 (Required) 

The International Standard Recording Code (ISRC) values for the music videos. You can substitute `filter[isrc]` for `ids`, or use it in conjunction with `ids` for additional filtering. Note that one ISRC value may return more than one music video. The maximum fetch limit is `25`.

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

MusicVideosResponse

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
https://api.music.apple.com/v1/catalog/us/music-videos?filter[isrc]=GB1302001140
```

```
{
    "data": [
        {
            "id": "1553279848",
            "type": "music-videos",
            "href": "/v1/catalog/us/music-videos/1553279848",
            "attributes": {
                "previews": [
                    {
                        "url": "https: //video-ssl.itunes.apple.com/itunes-assets/Video114/v4/c8/14/3c/c8143cb4-e58a-8075-44b0-602f43d7646f/mzvf_2953199973497507158.720w.h264lc.U.p.m4v",
                        "hlsUrl": "https: //play.itunes.apple.com/WebObjects/MZPlay.woa/hls/playlist.m3u8?cc=US&a=1553279848&id=231169237&l=en&aec=HD",
                        "artwork": {
                            "width": 1560,
                            "url": "https: //is3-ssl.mzstatic.com/image/thumb/Video124/v4/26/6b/fe/266bfe0f-9d0c-e992-ae86-ce97cb251e40/Job80599ed4-a39e-455a-9f99-5bdc54c44284-109334076-PreviewImage_preview_image_43000_video_sdr-Time1613053183818.png/{w}x{h}bb.jpeg",
                            "height": 1080,
                            "textColor3": "353c3d",
                            "textColor2": "181e1f",
                            "textColor4": "3b4445",
                            "textColor1": "101414",
                            "bgColor": "cadee0",
                            "hasP3": false
                        }
                    }
                ],
                "artwork": {
                    "width": 640,
                    "url": "https: //is1-ssl.mzstatic.com/image/thumb/Video124/v4/3f/1e/6f/3f1e6f35-6960-3f0e-0a0c-8701aa2012d4/dj.bcvxpufw.jpg/{w}x{h}mv.jpeg",
                    "height": 360,
                    "textColor3": "6b98c7",
                    "textColor2": "7cb0ea",
                    "textColor4": "638dbb",
                    "textColor1": "86bff9",
                    "bgColor": "000000",
                    "hasP3": false
                },
                "artistName": "Dua Lipa",
                "url": "https: //music.apple.com/us/music-video/were-good/1553279848",
                "genreNames": [
                    "Pop"
                ],
                "has4K": false,
                "durationInMillis": 191913,
                "releaseDate": "2021-02-12",
                "name": "We’re Good",
                "isrc": "GB1302001140",
                "playParams": {
                    "id": "1553279848",
                    "kind": "musicVideo"
                },
                "hasHDR": false
            },
            "relationships": {
                "artists": {
                    "href": "/v1/catalog/us/music-videos/1553279848/artists",
                    "data": [
                        {
                            "id": "1031397873",
                            "type": "artists",
                            "href": "/v1/catalog/us/artists/1031397873"
                        }
                    ]
                },
                "albums": {
                    "href": "/v1/catalog/us/music-videos/1553279848/albums",
                    "data": []
                }
            }
        }
    ],
    "meta": {
        "filters": {
            "isrc": {
                "GB1302001140": [
                    {
                        "id": "1552406856",
                        "type": "music-videos",
                        "href": "/v1/catalog/us/music-videos/1552406856"
                    },
                    {
                        "id": "1553279848",
                        "type": "music-videos",
                        "href": "/v1/catalog/us/music-videos/1553279848"
                    }
                ]
            }
        }
    }
}

```

## See Also

### Related Documentation

object MusicVideos

A resource object that represents a music video.

object MusicVideosResponse

The response to a music videos request.

### Requesting a Catalog Music Video

Get a Catalog Music Video

Fetch a music video by using its identifier.

Get a Catalog Music Video's Relationship Directly by Name

Fetch a music video’s relationship by using its identifier.

Get a Catalog Music Video’s Relationship View Directly by Name

Fetch related resources for a single music video’s relationship view.

Get Multiple Catalog Music Videos by ID

Fetch one or more music videos by using their identifiers.

Get Equivalent Catalog Music Videos by ID

Fetch the equivalent, available content in the storefront for the provided music videos’ identifiers.

