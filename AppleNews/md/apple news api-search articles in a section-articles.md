

- Apple News API
-  Search Articles in a Section 

Web Service Endpoint

# Search Articles in a Section

See a list of all articles in a section that match the specified search criteria.

Apple News API 1.0+

## URL

``` source
GET https://news-api.apple.com/sections/{sectionId}/articles
```

## Path Parameters

`sectionId`

`string`

 (Required) 

The UUID of the section to search.

## Query Parameters

`fromDate`

`string`

If specified, the server only returns articles with a `createdAt` date later than `fromDate`.

`pageSize`

`integer`

The number of articles to return on each page. This value must be an integer between 1 and 100 (inclusive).

Default: `10`

`pageToken`

`string`

An opaque token that specifies the page to view. The server returns links with the URL in each response. It also includes the `pageToken` for the next page.

`sortDir`

`string`

Indicates whether to return oldest articles first (`ASC`) or newest articles first (`DESC`).

Default: `DESC`

`toDate`

`string`

If specified, the server only returns articles with a `createdAt` date earlier than `toDate`.

## Response Codes

` 200 ``OK`

SearchResponse

`OK`

The request was successful.

Content-Type: application/json

` 400 ``Bad Request`

Error

`Bad Request`

- `MISSING`. You didn’t include the Channel UUID field in the request. Key path: \*

- `INVALID_TYPE`. The value you specified for `channelId` is not of the correct type for that field. Key path: `channelId`.

- `INVALID`. The `pageToken` parameter isn’t a valid token returned in a `next` link or `nextPageToken` field. Key path: `pageToken`

- `INVALID`. The `sortDir` parameter isn’t `ASC` or `DESC`. Key path: `sortDir`

- `INVALID`. The `fromDate` parameter isn’t in ISO 8601 date format. Key path: `fromDate`

- `INVALID`. The `toDate` parameter isn’t in ISO 8601 date format. Key path: `toDate.`

- `INVALID`. The `pageSize` parameter isn’t an integer in the range 1 to 100 (inclusive). Key path: `pageSize`.

Content-Type: application/json

` 401 ``Unauthorized`

Error

`Unauthorized`

You didn’t include the `Authorization` header. Key path: N/A

Content-Type: application/json

` 403 ``Forbidden`

Error

`Forbidden`

You tried to access a section your API key doesn’t have permission to access. Key path: N/A

Content-Type: application/json

` 404 ``Not Found`

Error

`Not Found`

- The endpoint you tried to access doesn’t exist. Key path: N/A.

- The section you tried to access doesn’t exist. Key path: `sectionId`.

Content-Type: application/json

` 429 ``Too Many Requests`

Error

`Too Many Requests`

You exceeded the number of articles that you can search for in a section within the specific time window. The response header `` indicates the time in seconds you need to wait before sending a new search request.

Content-Type: application/json

## Mentioned in 

Apple News API Release Notes for iOS 17, iPadOS 17, and macOS 14

## Discussion

A Search Articles request returns a list of all articles in a section that were created between `fromDate` and `toDate`. The results of this call are paginated, with a maximum page size of 100. Each response contains a link to the next page of results.

### Example

- Request
- Response

```
GET /sections/63a75491-2c4d-3530-af91-819be8c3ace0/articles?pageSize=2 HTTP/1.1
Host: news-api.apple.com
Accept: application/json
Authorization: HHMAC; key="1e3gfc5e-e9f8-4232-a6be-17bf40edad09"; signature="irqw07DCRQLtx/40Z2VhNc7sl3nB1PKII374R7AHjUQ="; date="2015-02-28T00:03:31Z"
```

```
HTTP/1.1 200 OK
Date: Thu, 19 Apr 2018 20:47:26 GMT
Request-Id: de2c85c0-4412-11e8-b019-43ff3ca2e49c
X-TEST-SOURCE-ENVIRONMENT: local
Content-Type: application/json;charset=utf-8
{
 "data": [
   {
     "createdAt": "2018-04-18T20:39:46Z",
     "modifiedAt": "2018-04-18T20:39:46Z",
     "id": "a329513d-2e32-438d-a056-15ab0e04f671",
     "type": "article",
     "shareUrl": "https://apple.news/AoylRPS4yQ42gVhWrDgT2cQ",
     "links": {
       "channel": "https://news-api.apple.com/channels/effd4d34-99b7-4abf-9f19-176d54f648ab",
       "self": "https://news-api.apple.com/articles/a329513d-2e32-438d-a056-15ab0e04f671",
       "sections": [
         "https://news-api.apple.com/sections/80deebc0-3b53-49cb-af3f-e91798b3dd10"
       ]
     },
     "revision": "AAAAAAAAAAD//////////w==",
     "state": "PROCESSING",
     "title": "Sample Article",
     "maturityRating": null,
     "warnings": [

     ],
     "isCandidateToBeFeatured": false,
     "isSponsored": false,
     "isPreview": false,
     "isDevelopingStory": false,
     "isHidden": false
   },
   {
     "createdAt": "2018-04-17T19:22:44Z",
     "modifiedAt": "2018-04-17T19:34:14Z",
     "id": "75594e44-5503-4c75-93a2-96c53a930672",
     "type": "article",
     "shareUrl": "https://apple.news/AdVlORFUDTHWTopbFOpMGcg",
     "links": {
       "channel": "https://news-api.apple.com/channels/effd4d34-99b7-4abf-9f19-176d54f648ab",
       "self": "https://news-api.apple.com/articles/75594e44-5503-4c75-93a2-96c53a930672",
       "sections": [
         "https://news-api.apple.com/sections/80deebc0-3b53-49cb-af3f-e91798b3dd10"
       ]
     },
     "revision": "AAAAAAAAAAD//////////w==",
     "state": "LIVE",
     "title": "Sample Article",
     "maturityRating": null,
     "warnings": [],
     "isCandidateToBeFeatured": false,
     "isSponsored": false,
     "isPreview": false,
     "isDevelopingStory": false,
     "isHidden": false
   },
 "links": {
   "next": "https://news-api.apple.com/sections/80deebc0-3b53-49cb-af3f-e91798b3dd10/articles?pageToken=AoJ%2FsvmP6eICPwUxYTkxOGRlMi0wMjM4LTQ4ZGQtOTE3Yy1lZDVlMThiMzhkYjQ%3D",
   "self": "https://news-api.apple.com/sections/80deebc0-3b53-49cb-af3f-e91798b3dd10/articles"
 },
 "meta": {
   "nextPageToken": "AoJ/svmP6eICPwUxYTkxOGRlMi0wMjM4LTQ4ZGQtOTE3Yy1lZDVlMThiMzhkYjQ="
 }
}
```

## See Also

### Articles

Create an Article

Publish an article to your channel.

Read Article Information

Retrieve information about an article, such as the revision number and maturity rating.

Search Articles in a Channel

See a list of all articles in a channel that match the specified search criteria.

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

