

- Device Management
- App and Book Management
- Apps and Books for Organizations
-  Handling requests and responses 

API Collection

# Handling requests and responses

Write a request for app or book metadata and handle responses from the API.

## Overview

Learn how to compose a request to get data from the Apps and Books for Organizations API and how to interpret responses.

### Compose a request

To compose a request, first specify the root path - `https://api.ent.apple.com/v1` for enterprise organizations, or `https://api.edu.apple.com/v1` for educational organizations.

Follow this part of the path with `/catalog/`, the storefront, and then any parameters that are specific to the endpoint. All requests must include the storefront in the path.

For example, to request information about a specific app, construct a URL that includes the ID of the app in the path:

```
GET https://api.ent.apple.com/v1/catalog/{storefront}/stoken-authenticated-apps?ids={id}&platform=iphone
```

You must also include the organization’s `sToken` as a cookie named `itvt` to access the `stoken-authenticated-apps` and `stoken-authenticated-books` endpoints.

Most requests return only the requested resource. For information about how to request related resources at the same time, see Fetching resources with extended attributes.

### Interpret a response

There are three kinds of responses: resource collection, results, and errors.

Results responses always have a top-level `results` member object that contains the information for the response. Results responses are always unique to the endpoint.

Error responses contain an array of one or more error objects that indicate any issues while handling the request. The status code of the response reflects the primary error. See Error and HTTP Status Codes.

Default responses for common requests include:

| **Request description** | **Status code** | **Response description** |
|----|----|----|
| Request for an existing single resource object | `200 (OK)` | The `data` array contains the requested resource object. |
| Request for a single resource object that doesn’t exist | `404 (Not Found)` | The response doesn’t contain a `data` array. |
| Request for multiple resource objects by ID | `200 (OK)` | The `data` array includes the existing resource objects. |
| Request for multiple resource objects by ID and none of the resources exist | `200 (OK)` | The `data` array is empty. |
| Request contains successfully modified or deleted resources | `204 (No Content)` | The body is empty. |
| A successful request to an endpoint that returns results | `200 (OK)` | The response includes the returned results. |
| The request isn’t accepted because its authorization is missing or invalid due to an issue with the developer token | `401 (Unauthorized)` | The response doesn’t contain a `data` array. |
| The request isn’t accepted due to an issue with the media user token or because the request is using incorrect authentication. | `403 (Forbidden)` | The response doesn’t contain a `data` array. |
| The request isn’t supported as specified | `400 (Bad Request)` | The `errors` array contains an error object for any identified problem. |
| The request encounters errors on the server | Any status code in the 500 range | The `errors` array contains error objects for the errors for any identified problem. |

## Topics

### Related Objects

object ResourceCollectionResponse

A response that contains the resource objects for the request.

object ResultsResponse

A response that contains the resource objects for the request.

object AppsResponse

A response that contains the resource objects for the request.

object BooksResponse

A response that contains the resource objects for the request.

object UnauthorizedResponse

A response that indicates an incorrect authorization header.

object ErrorsResponse

The collection of errors that occurred while processing the request.

## See Also

### Essentials

Generating developer tokens

Create a JSON Web Token to authorize your requests to the Apps and Books for Organizations API.

Fetching resources with extended attributes

Specify additional attributes for the API to include in a response.

Fetching storefront objects

Pick a region-specific geographic location to retrieve catalog information from.

Common Objects

Understand the common JSON objects that framework responses contain.

