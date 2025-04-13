

- Device Management
-  Get Metadata for Your Apps 

Web Service Endpoint

# Get Metadata for Your Apps

Fetch metadata for your apps by using their identifiers.

Device Assignment ServicesVPP License Management

## URL

``` source
GET https://api.ent.apple.com/v1/catalog/{storefront}/stoken-authenticated-apps
```

## Path Parameters

`storefront`

`string`

 (Required) 

An iTunes Store territory that you specify with an ISO 3166 alpha-2 country code. The possible values are the `id` attributes of `Storefrontobjects`.

## Query Parameters

`additionalPlatforms`

`[string]`

Additional platforms the app supports that you want to get metadata for.

Possible Values: `appletv, ipad, iphone, mac, realityDevice, web`

`extend`

`[string]`

A list of attribute extensions to apply to resources in the response. These attributes are usually more expensive, so only extend them if absolutely necessary.

Classifier (optional): A resource type to apply the parameter to, `apps` or `books`.\`\`

Possible Values: `description, fileSizeByDevice, languageList, latestVersionInfo, privacyPolicyUrl, requirementsByDeviceFamily, screenshotsByType, supportURLForLanguage, versionHistory, websiteUrl`

`ids`

`[string]`

The unique identifiers for the apps.

`l`

`string`

The localization to use, which you specify with a language tag. The possible values are in the `supportedLanguageTags` array belonging to the `Storefront` object that `storefront` specifies. Otherwise, the default is `defaultLanguageTag` in `Storefront`.

`platform`

`string`

 (Required) 

The platform the user-facing app is running on. You use this to get metadata for the specified platform.

Possible Values: `appletv, ipad, iphone, mac, realityDevice, web`

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

` 500 ``Internal Server Error`

ErrorsResponse

`Internal Server Error`

A response indicating an error occurred on the server.

Content-Type: application/json

## Discussion

### Example Request and Response

- Request
- Response

```
?ids=2001350931&platform=iphone
```

```
{
    "data": [
        {
            "attributes": {
                "artistName": "2K",
                "contentRatingsBySystem": {
                    "appsApple": {
                    "name": "Not yet rated",
                    "rank": 99,
                    "value": 600
                    }
                },
                "deviceFamilies": [
                    "mac",
                    "tvos",
                    "iphone",
                    "ipad",
                    "ipod"
                ],
                "genreDisplayName": "Entertainment",
                "hasEula": false,
                "isB2BCustomApp": false,
                "isFirstPartyHideableApp": false,
                "isVppDeviceBasedLicensingEnabled": true,
                "name": "App_67588039",
                "offers": [
                    {
                        "assets": [
                            {
                                "flavor": "iosSoftware",
                                "size": 2421760
                            }
                        ],
                        "buyParams": "productType=C&price=1990&salableAdamId=2001350931&pricingParameters=STDQ&pg=default&marketType=ENT&appExtVrsId=2000011304",
                        "currencyCode": "USD",
                        "price": 1.99,
                        "priceFormatted": "$1.99",
                        "type": "buy"
                    }
                ],
                "platformAttributes": {
                    "ios": {
                        "artwork": {
                            "bgColor": "ffffff",
                            "height": 1024,
                            "textColor1": "170502",
                            "textColor2": "431207",
                            "textColor3": "453735",
                            "textColor4": "684138",
                            "url": "https://isq11.mzstatic.com/image/thumb/Purple62/v4/e5/88/8e/e5888e16-ca3a-3ba4-ec46-d1c1091f4104/AppIcon-1x_U007emarketing-0-7-0-85-220.png/{w}x{h}bb.{f}",
                            "width": 1024
                        },
                        "bundleId": "com.67588039",
                        "externalVersionId": 2000011304,
                        "minimumOSVersion": "13.0",
                        "requiredCapabilities": "arm64 ",
                        "seller": "2K Sports"
                    }
                },
                "supportsDeviceSharing": false,
                "url": "https://apps.apple.com/us/app/app-67588039/id2001350931",
                "userRating": {
                    "ratingCount": 0,
                    "value": 0
                },
                "usesClassKit": false
            },
            "href": "/v1/catalog/us/apps/2001350931",
            "id": "2001350931",
            "relationships": {
                "genres": {
                    "data": [
                        {
                            "attributes": {
                                "name": "Entertainment",
                                "parentId": "36",
                                "parentName": "App Store",
                                "url": "https://itunes.apple.com/us/genre/id6016"
                            },
                            "href": "/v1/catalog/us/genres/6016",
                            "id": "6016",
                            "type": "genres"
                        }
                    ],
                    "href": "/v1/catalog/us/apps/2001350931/genres"
                }
            },
            "type": "apps"
        }
    ]
}
```

## Topics

### Responses

object ResourceCollectionResponse

A response that contains the resource objects for the request.

object UnauthorizedResponse

A response that indicates an incorrect authorization header.

object ErrorsResponse

The collection of errors that occurred while processing the request.

## See Also

### App and book metadata

Get Metadata for Your Books

Fetch metadata for your books by using their identifiers.

Get Metadata for a Catalog App

Fetch metadata for an app from the catalog by using its identifier.

Get Metadata for Multiple Catalog Apps

Fetch metadata for apps from the catalog by using their identifiers.

Get Metadata for a Catalog Book

Fetch metadata for a book from the catalog by using its identifier.

Get Metadata for Multiple Catalog Books

Fetch metadata for books from the catalog by using their identifiers.

Get Catalog Search Results

Fetch metadata for apps and books from the catalog by using a search term.

