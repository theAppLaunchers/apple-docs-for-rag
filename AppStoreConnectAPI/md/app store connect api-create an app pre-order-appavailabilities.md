

- App Store Connect API
-  Create an App Pre-Order 

Web Service Endpoint

# Create an App Pre-Order

Create an app pre-order and set the expected app release date.

App Store Connect API 3.0+

## URL

``` source
POST https://api.appstoreconnect.apple.com/v2/appAvailabilities
```

## HTTP Body

AppAvailabilityV2CreateRequest

Content-Type: application/json

## Response Codes

` 201 ``Created`

AppAvailabilityV2Response

`Created`

Content-Type: application/json

` 400 ``Bad Request`

ErrorResponse

`Bad Request`

Content-Type: application/json

` 401 ``Unauthorized`

ErrorResponse

`Unauthorized`

Content-Type: application/json

` 403 ``Forbidden`

ErrorResponse

`Forbidden`

Content-Type: application/json

` 409 ``Conflict`

ErrorResponse

`Conflict`

Content-Type: application/json

` 422 `

ErrorResponse

Content-Type: application/json

## Mentioned in 

App Store Connect API 3.1 release notes

## See Also

### Managing app and territory availability

Read App Availabilty

Get information about your app’s availalbility.

Read App Availablity Territories

Read the territory availablity for a specific app.

Modify the Territory Availabilty for an App Pre-Order

Update the release territories for your app pre-order.

End an App Pre-Order

End the pre-order for your app and release to store immediately.

