

- App Store Connect API
- Interpreting and Handling Errors
-  About the HTTP Status Code 

Article

# About the HTTP Status Code

Learn how the status code helps you determine if an App Store Connect API request succeeded or why it failed.

## Overview

The codes the API returns are defined by the HTTP standard and fall in these meaningful ranges:

- 200s: The request succeeded.

- 400s: The request failed due to an error in the request.

- 500s: The request failed due to a server-side error.

The following table lists the HTTP status codes and the reasons why App Store Connect API may return them.

| HTTP Status Code | Name | Description |
|----|----|----|
| 200 | OK | The request was successful and response data was returned. |
| 201 | Created | The request to create a resource was successful and response data was returned. The location header contains the created resource’s URI. |
| 204 | No Content | The request was successful and no response data is needed. |
| 400 | Bad Request | The request is invalid and cannot be accepted. |
| 403 | Forbidden | The request is not allowed. This can happen if your API key is revoked, your token is incorrectly formatted, or if the requested operation is not allowed. |
| 404 | Not Found | The request cannot be fulfilled because the resource does not exist. |
| 405 | Method Not Allowed | The request cannot be accepted because the HTTP method is not appropriate for the given URI. |
| 406 | Not Acceptable | The request cannot be accepted because the `Accept` header requires a media type the API does not support.  The response in this case is in plain text, not JSON. |
| 409 | Conflict | The request cannot be accepted because the JSON data you have provided conflicts with rules enforced by the API. |
| 410 | Gone | The request cannot be fulfilled because the requested resource, which is known to have previously existed, no longer exists. Usually this case results in a 404 status code, but when knowledge that a resource previously existed is important, the API returns a 410. This happens, for instance, if you request a user invitation after the user accepted the invitation. |
| 415 | Unsupported Media Type | The request cannot be accepted because the media type of the request entity is not a format the API understands. Make sure the `Content-Type` header in the request is `application/json`. |
| 422 | Unprocessable Entity | The request cannot be accepted because the data you provided is not valid JSON or is not expected for the request. |
| 429 | Too Many Requests | The request cannot be accepted because you have exceeded the rate limit for your API key. You will need to wait awhile and try the request again. |
| 500 | Internal Server Error | The request failed. This may be due to a temporary outage. Check the Apple Developer System Status Page for up to date information on the App Store Connect API. |

If the request fails, use the additional data provided in the ErrorResponse to determine how to respond to the error.

## See Also

### Handling Errors

Parsing the Error Response Code

Interpret the error details to troubleshoot API requests and perform programmatic error handling.

Pinpointing the Location of Errors

Locate the specific source of the error.

