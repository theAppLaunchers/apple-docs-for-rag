

- Apple Music API
-  Get a Library Music Video's Relationship Directly by Name 

Web Service Endpoint

# Get a Library Music Video's Relationship Directly by Name

Fetch a library music video’s relationship by using its identifier.

Apple Music 1.0+

## URL

``` source
GET https://api.music.apple.com/v1/me/library/music-videos/{id}/{relationship}
```

## Path Parameters

`id`

`string`

 (Required) 

The unique identifier for the library music video.

`relationship`

`string`

 (Required) 

The name of the relationship you want to fetch for this resource.

Possible Values: `albums, artists, catalog`

## Query Parameters

`l`

`string`

The localization to use, specified by a language tag. The possible values are in the `supportedLanguageTags` array belonging to the `Storefront` object specified by `storefront`. Otherwise, the default is `defaultLanguageTag` in `Storefront`.

`include`

`[string]`

Additional relationships to include in the fetch.

`limit`

`integer`

The number of objects or number of objects in the specified relationship returned.

Default: `25`

Maximum: `100`

`extend`

`[string]`

A list of attribute extensions to apply to resources in the response.

## Response Codes

` 200 ``OK`

RelationshipResponse

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
https://api.music.apple.com/v1/me/library/music-videos/i.V7B9dQLsZ8DZKe/catalog
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
                        "url": "https://video-ssl.itunes.apple.com/itunes-assets/Video114/v4/c8/14/3c/c8143cb4-e58a-8075-44b0-602f43d7646f/mzvf_2953199973497507158.720w.h264lc.U.p.m4v",
                        "hlsUrl": "https://play.itunes.apple.com/WebObjects/MZPlay.woa/hls/playlist.m3u8?cc=US&a=1553279848&id=231169237&l=en&aec=HD",
                        "artwork": {
                            "width": 1560,
                            "height": 1080,
                            "url": "https://is3-ssl.mzstatic.com/image/thumb/Video124/v4/26/6b/fe/266bfe0f-9d0c-e992-ae86-ce97cb251e40/Job80599ed4-a39e-455a-9f99-5bdc54c44284-109334076-PreviewImage_preview_image_43000_video_sdr-Time1613053183818.png/{w}x{h}bb.jpeg",
                            "bgColor": "cadee0",
                            "textColor1": "101414",
                            "textColor2": "181e1f",
                            "textColor3": "353c3d",
                            "textColor4": "3b4445"
                        }
                    }
                ],
                "artwork": {
                    "width": 640,
                    "height": 360,
                    "url": "https://is1-ssl.mzstatic.com/image/thumb/Video124/v4/3f/1e/6f/3f1e6f35-6960-3f0e-0a0c-8701aa2012d4/dj.bcvxpufw.jpg/{w}x{h}mv.jpeg",
                    "bgColor": "000000",
                    "textColor1": "86bff9",
                    "textColor2": "7cb0ea",
                    "textColor3": "6b98c7",
                    "textColor4": "638dbb"
                },
                "artistName": "Dua Lipa",
                "url": "https://music.apple.com/us/music-video/were-good/1553279848",
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
            }
        }
    ]
}

```

## See Also

### Related Documentation

object LibraryMusicVideos

A resource object that represents a library music video.

object LibraryMusicVideosResponse

The response to a library music videos request.

### Requesting a Library Music Video

Get a Library Music Video

Fetch a library music video by using its identifier.

Get Multiple Library Music Videos

Fetch one or more library music videos by using their identifiers.

Get All Library Music Videos

Fetch all the library music videos in alphabetical order.

