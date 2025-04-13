

- Apple News API
-  Read Article Information 

Web Service Endpoint

# Read Article Information

Retrieve information about an article, such as the revision number and maturity rating.

Apple News API 1.0+

## URL

``` source
GET https://news-api.apple.com/articles/{articleId}
```

## Path Parameters

`articleId`

`string`

 (Required) 

The UUID or the Share URL ID of the article to get.

## Response Codes

` 200 ``OK`

ArticleResponse

`OK`

- The request was successful.

- The Apple News team optimized the article. Contact your Apple News technical representative if you need to update or delete the article.

Content-Type: application/json

` 400 ``Bad Request`

Error

`Bad Request`

- `MISSING`. You didn’t include the Article UUID or the Share URL ID field in the request. Key path: `articleId.`

- `INVALID_TYPE`. The value you specified for the article is not of the correct type for that field. Key path: `articleId`.

Content-Type: application/json

` 401 ``Unauthorized`

Error

`Unauthorized`

You didn’t include the `Authorization` header. Key path: N/A

Content-Type: application/json

` 403 ``Forbidden`

Error

`Forbidden`

You tried to access an article your API key doesn’t have permission to access. Key path: N/A

Content-Type: application/json

` 404 ``Not Found`

Error

`Not Found`

- The endpoint you tried to access doesn’t exist. Key path: N/A

- The article you tried to access doesn’t exist. Key path: `articleId`.

Content-Type: application/json

## Mentioned in 

Apple News API Release Notes for iOS 17, iPadOS 17, and macOS 14

## Discussion

Use the Read Article Information endpoint to retrieve information about the article (Article), article links (`ArticleLinks`), meta (Meta), and optional metadata fields (Create Article Metadata Fields).

### Example

- Request
- Response

```
GET /articles/a3caeb08-b9db-4002-b379-cde305d74be7 HTTP/1.1
Host: news-api.apple.com
Accept: application/json
Authorization: HHMAC; key="1e3gfc5e-e9f8-4232-a6be-17bf40edad09"; signature="irqw07DCRQLtx/40Z2VhNc7sl3nB1PKII374R7AHjUQ="; date="2015-02-28T00:03:31Z"
```

```

HTTP/1.1 200 OK
Date: Sat, 28 Feb 2015 00:51:41 GMT
Content-Type: application/json;charset=UTF-8
Transfer-Encoding: chunked
{
  "data": {
    "createdAt": "2015-02-28T00:49:36Z",
    "modifiedAt": "2015-02-28T00:49:36Z",
    "id": "a3caeb08-b9db-4002-b379-cde305d74be7",
    "type": "article",
    "shareUrl": "https://apple.news/ArRPpLPE9QXu3sehS0rvxvA",
    "links": {
      "channel": "https://news-api.apple.com/channels/63a75491-2c4d-3530-af91-819be8c3ace0",
      "self": "https://news-api.apple.com/articles/a3caeb08-b9db-4002-b379-cde305d74be7",
      "sections": [
        "https://news-api.apple.com/sections/0a468272-356f-3b61-afa3-c4f989954180",
        "https://news-api.apple.com/sections/0a664711-242f-6b13-1fa1-a6f081549989"
      ]
    },
  "document": {
  "version": "1.7",
  "identifier": "SampleArticle",
  "language": "en",
  "title": "Apple News App",
  "subtitle": "A look at the features of the News iOS app",
  "layout": {
    "columns": 7,
    "width": 1024,
    "margin": 75,
    "gutter": 20
  },
  "components": [
    {
      "role": "title",
      "text": "Apple News App",
      "textStyle": "title"
    },
    {
      "role": "body",
      "text": "The Apple News Format allows publishers to craft beautiful editorial layouts. Galleries, audio, video, and fun interactions like animation make stories spring to life."
    },
    {
      "role": "photo",
      "URL": "bundle://image.jpg"
    }
  ],
  "documentStyle": {
    "backgroundColor": "#F7F7F7"
  },
  "componentTextStyles": {
    "default": {
      "fontName": "Helvetica",
      "fontSize": 13,
      "linkStyle": {
        "textColor": "#428bca"
      }
    },
    "title": {
      "fontName": "Helvetica-Bold",
      "fontSize": 30,
      "hyphenation": false
    },
    "default-body": {
      "fontName": "Helvetica",
      "fontSize": 13
    }
  }
  },
"revision": "AAAAAAAAAAAAAAAAAAAAew==",
"state": "PROCESSING",
"title": "Tie Goes to the Runner",
"maturityRating": null,
"warnings": [],
"isCandidateToBeFeatured": false,
"isSponsored": false,
"isPreview": false,
"targetTerritoryCountryCodes": ["GB", "US"]
}
}
```

## See Also

### Articles

Create an Article

Publish an article to your channel.

Search Articles in a Channel

See a list of all articles in a channel that match the specified search criteria.

Search Articles in a Section

See a list of all articles in a section that match the specified search criteria.

Update an Article

Update an existing article in your channel.

Delete an Article

Delete the specified article from your channel.

object Create Article Metadata Fields

See the optional metadata fields for the Create an Article Request.

object ArticleLinksRequest

See the required field for the Create an Article request.

object Update Article Metadata Fields

See the metadata fields for the Update an Article request.

object Article

See the fields the article endpoints returned.

object ArticleResponse

See which objects make up the Create an Article, Read an Article, and Update an Article responses.

object ArticleLinksResponse

See the links the article endpoints returned.

object SearchResponse

See the fields the search article endpoints returned.

object Meta

See the object that wraps the throttling information that’s returned for the Create an Article and Read an Article endpoints.

object Throttling

See the object that wraps the throttling information that’s returned for the Create an Article and Update an Article endpoints.

