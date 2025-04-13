

- Apple Search Ads
-  Get Product Page Locales 

Web Service Endpoint

# Get Product Page Locales

Fetches product page locales by identifier.

Search Ads 5.0+

## URL

``` source
GET https://api.searchads.apple.com/api/v5/apps/{adamId}/product-pages/{productPageId}/locale-details
```

## Path Parameters

`adamId`

`int64`

 (Required) 

Your unique App Store app identifier.

Your `adamId` in the resource path must match the `adamId` in your campaign. Use Get a Campaign or Get all Campaigns to obtain your `adamId` and correlate it to the correct campaign.

`productPageId`

`string`

 (Required) 

A unique string to identify a product page on App Store Connect. For example, `45812c9b-c296-43d3-c6a0-c5a02f74bf6e`.

## Query Parameters

`deviceClasses`

`string`

Filters by device type.

Possible Values: `IPAD, IPHONE`

`expand`

`boolean`

Detailed app asset details of a device. Use `true` for expanded values in the API response.

Default: `false`

`languageCodes`

`string`

Filters by ISO 639-1 language code appended to the ISO alpha-2 country code, such as `en-US`. The `languageCodes` paramater can have multiple values such as `en-US`, `fr-CA`.

`languages`

`string`

Filters by ISO alpha-2 country code, such as `US`.

## Response Codes

` 200 ``OK`

ProductPageLocaleDetailListResponse

`OK`

If the call succeeds, the API returns the ProductPageLocaleDetailListResponse object in the response payload with an HTTP status code of `200(OK)`. If unsuccessful, the HTTP status code indicates the error with details in the error message.

Content-Type: application/json

` 400 ``Bad Request`

ApiErrorResponse

`Bad Request`

An invalid query or missing required parameters.

Content-Type: application/json

` 401 ``Unauthorized`

ApiErrorResponse

`Unauthorized`

An unauthenticated call fails to get the requested response.

Content-Type: application/json

` 403 ``Forbidden`

ApiErrorResponse

`Forbidden`

Insufficient rights to the resource.

Content-Type: application/json

` 404 ``Not Found`

ApiErrorResponse

`Not Found`

The API can’t locate the resource.

Content-Type: application/json

` 429 `

ApiErrorResponse

The API calls exceed rate-limit thresholds. See the Rate Limits subsection of Calling the Apple Search Ads API.

Content-Type: application/json

` 500 ``Internal Server Error`

ApiErrorResponse

`Internal Server Error`

The Apple Search Ads server is temporarily down or unreachable. The request may be valid, but you need to retry it later.

Content-Type: application/json

## Discussion

Use this endpoint to return localized product page metadata using your `adamId` and `productPageId` in the resource path.

### Payload example: Get product page locales

- Request
- Response

```
GET https://api.searchads.apple.com/api/v5/apps/{adamId}/product-pages/{productPageId}/locale-details
```

```
{
  "adamId": 1408851466,
  "productPageId": "45812c9b-c296-43d3-c6a0-c5a02f74bf6e0",
  "language": "en",
  "appName": "Trip Trek",
  "languageCode": "en-US",
  "subTitle": "Updated for iOS 15",
  "promotionalText": "The best travel app for iOS.",
  "shortDescription": "A cartographic dashboard to track your awesome treks.",
  "deviceClasses": [
    "IPHONE"
  ]
}
```

### Payload example: Expanded format

- Request
- Response

```
GET https://api.searchads.apple.com/api/v5/apps/{adamId}/product-pages/{productPageId}/locale-details?expand=true
```

```
{
  "adamId": 1407651474,
  "productPageId": "63cbf98e-f2a4-453a-9215-71084a273992",
  "language": "es",
  "appName”: “Trip Trek”,
  "languageCode": "es-MX",
  "subTitle": "Actualizado para iOS 15",
  "promotionalText": "iLa mejor aplicación de viajes para iOS.",
  "shortDescription": "Un tablero cartográfico para realizar un seguimiento de sus increíbles caminatas.",
  "deviceClasses": [
    "IPHONE"
  ],
  "appPreviewDeviceWithAssets": {
    "iphone6+": {
      "appPreviewDeviceFallBackDevices": [
        "iphone6",
        "iphone5"
      ],
      "screenshots": [
        {
          "assetGenId”: “1408851466;es-MX;5;0;6d16a47cbc2b3aba0664f87fffd20a92",
          "assetUrl”: “https://is5-ssl.mzstatic.com/image/thumb/source113/v4/25/f5/70/25f57023-87bd-25f0-71dc-bf5f48525b4c/afcd3ec4-d7af-49c5-9d93-44084b0abea8_2208x1242iphone55_4.jpg/2208x1242.jpg",
          "sortPosition": 1,
          "sourceHeight": 2208,
          "sourceWidth": 1242,
          "orientation": "PORTRAIT",
          "assetType”: “SCREENSHOT"
        },
        {
          "assetGenId”: “1408851466;es-MX;5;0;de730d1f14111eecc3c9bc534e70675e",
          "assetUrl”: “https://is5-ssl.mzstatic.com/image/thumb/source113/v4/e9/83/f9/e983f933-6db2-c68c-531e-bcecf84cb490/ad9be53d-1fc0-42f0-95be-0a1da78ffd73_1242x2208iphone55_6.jpg/2208x1242.jpg",
          "sortPosition": 2,
          "sourceHeight": 2208,
          "sourceWidth": 1242,
          "orientation": "PORTRAIT",
          "assetType”: “SCREENSHOT"
        },
        {
          "assetGenId”: “1408851466;es-MX;5;0;cc08e766f8b27ab1715a0cff6522415a",
          "assetUrl”: “https://is5-ssl.mzstatic.com/image/thumb/Source123/v4/bb/bd/a7/bbbda7fb-f73b-694b-a330-ee43309686ac/b275b78f-2371-4203-9667-12ed97cf22f7_1242x2208iphone55_5.jpg/2208x1242.jpg",
          "sortPosition": 3,
          "sourceHeight": 2208,
          "sourceWidth": 1242,
          "orientation": "PORTRAIT",
          "assetType”: “SCREENSHOT"
        },
        {
          "assetGenId”: “1408851466;es-MX;5;0;6d16a47cbc2b3aba0664f87fffd20a92",
          "assetUrl”: “https://is5-ssl.mzstatic.com/image/thumb/source123/v4/43/31/20/43312040-79c9-602a-f21c-8256c9e40aa6/26c621b3-2e58-4992-9334-ce85ccb3af7c_1242x2208iphone55_4.jpg/2208x1242.jpg",
          "sortPosition": 4,
          "sourceHeight": 2208,
          "sourceWidth": 1242,
          "orientation": "PORTRAIT",
          "assetType": "SCREENSHOT"
        }
      ],
      "appPreviews": [
        {
          "assetGenId": "1408851466;es-MX;5;1;3a5af62d592e13a15520f883c3ff7c90",
          "assetUrl”: “https://is5-ssl.mzstatic.com/image/thumb/video123/v4/e7/c9/0d/e7c90d0d-ae42-f4a6-585e-aca9cfff68f9/Job27415bc0-a312-47a1-ba3d-c6d9fff9f395-2000195885-PreviewImage_PreviewImageIntermediate_preview_image_nonvideo_vfcs2000244409-Time1636676743709.png/1920x1080.jpg",
          "sortPosition": 1,
          "sourceHeight": 1920,
          "sourceWidth": 1080,
          "orientation": "PORTRAIT",
          "assetType": "APP_PREVIEW"
        }
      ]
    }
  }
}
```

## See Also

### Product Page Endpoints

Get Product Pages

Fetches metadata of all your custom product pages.

Get Product Pages by Identifier

Fetches metadata for a specific product page.

Get Supported Countries or Regions

Fetches supported languages and language codes.

Get App Preview Device Sizes

Fetches supported app preview device-size mappings.

