

- Device Management
-  Get Users 

Web Service Endpoint

# Get Users

Get information about a set of users.

Device Assignment ServicesVPP License Management

## URL

``` source
GET https://vpp.itunes.apple.com/mdm/v2/users
```

## Query Parameters

`activeOnly`

`boolean`

The filter for only the active users.

`clientUserId`

`string`

The filter for the unique identifier of a user in your organization.

`pageIndex`

`int32`

The requested page index.

`retiredOnly`

`boolean`

The filters for only the retired users.

`sinceVersionId`

`string`

The filter for modified assignments since the specified version identifier.

## Response Codes

` 200 ``OK`

GetUsersResponse

`OK`

Content-Type: application/json

` 400 ``Bad Request`

ErrorResponse

`Bad Request`

Content-Type: application/json

` 401 ``Unauthorized`

ErrorResponse

`Unauthorized`

The provided token is invalid. It may either be missing or expired.

Content-Type: application/json

` 500 ``Internal Server Error`

ErrorResponse

`Internal Server Error`

An internal server error occurred. Try again later.

Content-Type: application/json

## Mentioned in 

Managing Apps and Books Through Web Services

Upgrading to the new App and Book Management API

Using Paginated Endpoints

Managing Users

## Discussion

### Example Request and Response

- Request
- Response

```
?activeOnly=true
```

```
{
    "currentPageIndex": 0,
    "size": 3,
    "tokenExpirationDate": "2030-11-08T22:33:22+0000",
    "totalPages": 1,
    "uId": "2049025000431439",
    "users": [
        {
            "clientUserId": "client-101",
            "email": "client-101@apple.com",
            "inviteCode": "46bc93ea3acd41e0a4919c02db0d7d3a",
            "status": "Registered"
        },
        {
            "clientUserId": "client-102",
            "email": "client-102@apple.com",
            "inviteCode": "d2ab1319ff6448f89bb1b0e010cf68e0",
            "status": "Registered"
        },
        {
            "clientUserId": "client-103",
            "email": "client-1031@apple.com",
            "status": "Retired"
        }
    ],
    "versionId": "021f10a0-7035-11eb-9f67-bd1df52e1e13"
}
```

## Topics

### Response

object GetUsersResponse

The paginated response that contains the requested users.

object ErrorResponse

The response that contains the error that occurs.

## See Also

### User Management

Create Users

Create users to assign apps and books to.

Update Users

Update details for existing users.

Retire Users

Retire users by client user IDs.

