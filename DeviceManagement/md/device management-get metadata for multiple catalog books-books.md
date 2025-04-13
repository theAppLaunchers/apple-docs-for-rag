

- Device Management
-  Get Metadata for Multiple Catalog Books 

Web Service Endpoint

# Get Metadata for Multiple Catalog Books

Fetch metadata for books from the catalog by using their identifiers.

Device Assignment ServicesVPP License Management

## URL

``` source
GET https://api.ent.apple.com/v1/catalog/{storefront}/books#ids
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

`ids`

`[string]`

 (Required) 

The unique identifiers for the catalog books. The maximum fetch limit is 150.

`include`

`[string]`

A list of relationship names to include for resources in the response.

Classifier (optional): A resource type to apply the parameter to, `apps` or `books`.

`l`

`string`

The localization to use, which you specify with a language tag. The possible values are in the `supportedLanguageTags` array belonging to the `Storefront` object that `storefront` specifies. Otherwise, the default is `defaultLanguageTag` in `Storefront`.

`platform`

`string`

 (Required) 

The platform the user-facing app is running on. You use this to get metadata for the specified platform.

Possible Values: `appletv, ipad, iphone, mac, realityDevice, web`

`relate`

`[string]`

A list of relationship names to relate for resources in the response.

Classifier (optional): A resource type to apply the parameter to, `apps` or `books`.

## Response Codes

` 200 ``OK`

BooksResponse

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
?ids=510907372,1378977317&platform=iphone
```

```
{
  "data": [
    {
      "id": "510907372",
      "type": "books",
      "href": "/v1/catalog/us/books/510907372",
      "attributes": {
        "offers": [
          {
            "buyParams": "productType=PUB&price=0&salableAdamId=510907372&pricingParameters=PLUS&pg=default&marketType=EDU",
            "type": "get",
            "priceFormatted": "$0.00",
            "price": 0,
            "currencyCode": "USD",
            "assets": [
              {
                "flavor": "plusPublication",
                "size": 52007
              }
            ]
          }
        ],
        "genreNames": [
          "Poetry",
          "Books",
          "Fiction & Literature"
        ],
        "name": "book",
        "artistName": "author",
        "artwork": {
          "width": 665,
          "height": 982,
          "url": "https://isq11.mzstatic.com/image/thumb/Publication7/v4/75/e6/59/75e65967-4481-f194-6ce8-fe0ee69bc5bf/coverArt.9e3ac1.jpg/{w}x{h}bb.{f}",
          "bgColor": "aa0500",
          "textColor1": "fff8fa",
          "textColor2": "efab9d",
          "textColor3": "edc7c8",
          "textColor4": "e18a7e"
        },
        "url": "https://books.apple.com/us/book/name/id510907372",
        "userRating": {
          "value": 0,
          "ratingCount": 0
        }
      },
      "relationships": {
        "genres": {
          "href": "/v1/catalog/us/books/510907372/genres",
          "data": [
            {
              "id": "10093",
              "type": "genres",
              "href": "/v1/catalog/us/genres/10093",
              "attributes": {
                "parentName": "Fiction & Literature",
                "name": "Poetry",
                "parentId": "9031",
                "url": "https://itunes.apple.com/us/genre/id10093"
              }
            },
            {
              "id": "38",
              "type": "genres",
              "href": "/v1/catalog/us/genres/38",
              "attributes": {
                "name": "Books",
                "url": "https://itunes.apple.com/us/genre/id38"
              }
            },
            {
              "id": "9031",
              "type": "genres",
              "href": "/v1/catalog/us/genres/9031",
              "attributes": {
                "parentName": "Books",
                "name": "Fiction & Literature",
                "parentId": "38",
                "url": "https://itunes.apple.com/us/genre/id9031"
              }
            }
          ]
        }
      }
    },
    {
      "id": "1378977317",
      "type": "books",
      "href": "/v1/catalog/us/books/1378977317",
      "attributes": {
        "offers": [
          {
            "buyParams": "productType=PUB&price=33990&salableAdamId=1378977317&pricingParameters=STDQ&pg=default&marketType=EDU",
            "type": "buy",
            "priceFormatted": "$33.99",
            "price": 33.99,
            "currencyCode": "USD",
            "assets": [
              {
                "flavor": "publication",
                "size": 4569258
              }
            ]
          }
        ],
        "genreNames": [
          "Biographies & Memoirs",
          "Books"
        ],
        "isbn": "9788233801021",
        "name": "bob",
        "artistName": "artistname",
        "artwork": {
          "width": 1600,
          "height": 2414,
          "url": "https://isq11.mzstatic.com/image/thumb/Publication128/v4/49/b2/0e/49b20e3a-43f6-6a06-d351-8eed123ff336/9788233801021_H2_Harry_En_biografi_om_prinsen_Cover.jpg/{w}x{h}bb.{f}",
          "bgColor": "eaedf2",
          "textColor1": "0d0d11",
          "textColor2": "3d312b",
          "textColor3": "393a3e",
          "textColor4": "605752"
        },
        "url": "https://books.apple.com/us/book/harry/id1378977317",
        "userRating": {
          "value": 0,
          "ratingCount": 0
        }
      },
      "relationships": {
        "genres": {
          "href": "/v1/catalog/us/books/1378977317/genres",
          "data": [
            {
              "id": "9008",
              "type": "genres",
              "href": "/v1/catalog/us/genres/9008",
              "attributes": {
                "parentName": "Books",
                "name": "Biographies & Memoirs",
                "parentId": "38",
                "url": "https://itunes.apple.com/us/genre/id9008"
              }
            },
            {
              "id": "38",
              "type": "genres",
              "href": "/v1/catalog/us/genres/38",
              "attributes": {
                "name": "Books",
                "url": "https://itunes.apple.com/us/genre/id38"
              }
            }
          ]
        }
      }
    }
  ]
}
```

## Topics

### Responses

object BooksResponse

A response that contains the resource objects for the request.

object UnauthorizedResponse

A response that indicates an incorrect authorization header.

object ErrorsResponse

The collection of errors that occurred while processing the request.

## See Also

### App and book metadata

Get Metadata for Your Apps

Fetch metadata for your apps by using their identifiers.

Get Metadata for Your Books

Fetch metadata for your books by using their identifiers.

Get Metadata for a Catalog App

Fetch metadata for an app from the catalog by using its identifier.

Get Metadata for Multiple Catalog Apps

Fetch metadata for apps from the catalog by using their identifiers.

Get Metadata for a Catalog Book

Fetch metadata for a book from the catalog by using its identifier.

Get Catalog Search Results

Fetch metadata for apps and books from the catalog by using a search term.

