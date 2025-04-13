

- App Store Server API
-  CheckTestNotificationResponse 

Object

# CheckTestNotificationResponse

A response that contains the contents of the App Store server’s test notification and the result from your server.

App Store Server API 1.5+

``` source
object CheckTestNotificationResponse
```

## Properties

`sendAttempts`

`[`sendAttemptItem`]`

An array of information the App Store server records for its attempts to send the `TEST` notification to your server. The array may contain a maximum of six sendAttemptItem objects.

`signedPayload`

signedPayload

The signed payload, in JWS format, that contains the `TEST` notification that the App Store server sent to your server.

`firstSendAttemptResult`

`string`

Deprecated 

The result of the App Store server’s first attempt to send the `TEST` notification to your server.

Use the first sendAttemptItem in the `sendAttempts` array instead.

## Mentioned in 

App Store Server API changelog

## Discussion

The Get Test Notification Status endpoint returns this response.

The `sendAttempts` array contains up to six sendAttemptItem items: one for the initial attempt, and up to five for the retries. Use this information to troubleshoot your server if it doesn’t receive notifications at its App Store Server Notifications V2 endpoint successfully.

The `signedPayload` contains the `TEST` notification that the App Store server attempted to send to your server.

## Topics

### Data types

object sendAttemptItem

The success or error information and the date the App Store server records when it attempts to send a server notification to your server.

type signedPayload

A cryptographically signed payload, in JSON Web Signature (JWS) format, containing the response body for a version 2 notification.

## See Also

### App Store Server Notifications testing

Request a Test Notification

Ask App Store Server Notifications to send a test notification to your server.

Get Test Notification Status

Check the status of the test App Store server notification sent to your server.

object SendTestNotificationResponse

A response that contains the test notification token.

