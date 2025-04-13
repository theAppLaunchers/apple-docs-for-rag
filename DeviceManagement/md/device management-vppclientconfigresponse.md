

- Device Management
-  VppClientConfigResponse 

Object

# VppClientConfigResponse

The response that contains the client configuration.

Device Assignment ServicesVPP License Management

``` source
object VppClientConfigResponse
```

## Properties

`apnToken`

`string`

The Apple Push Notification token to use for notifications.

`appleId`

`string`

The AppleID associated with the provided sToken.

`clientContext`

`string`

The value currently associated with the provided sToken. This field is only included in the response when a value has been set via the Client Configuration endpoint.

See Protecting Your VPP Account for more information.

`countryCode`

`string`

The two-letter ISO 3166-1 code that designates the country where the VPP account is located. For example, `US` stands for United States, `CA` for Canada, `JP` for Japan, and so on.

`defaultPlatform`

`string`

The value to be passed for the platform parameter in the `contentMetadataLookupUrl` request. Possible values are:

- `volumestore`: For apps in the educational store.

- `enterprisestore`: For apps in the enterprise store.

See Getting App and Book Information (Legacy) for more information.

`email`

`string`

The email address associated with the provided sToken.

`errorMessage`

`string`

The human-readable explanation of the error.

`errorNumber`

`int32`

The numeric code of the error.

`expirationMillis`

`int64`

The UNIX epoch timestamp, in milliseconds, when the account’s sToken or password expires (whichever is earlier).

`location`

VppLocation

The location associated with the provided sToken. This field is only returned when a location token is used with an Apple School Manager account.

`organizationId`

`string`

The unique identifier assigned to an organization by the VPP.

`organizationIdHash`

`string`

The hash of `organizationId`.

`status`

`int32`

The status code for the response. Possible values are:

- `0` = Success.

- `-1` = Failure.

`uId`

`string`

The unique library identifier. When querying records using multiple tokens that may share libraries, use the `uId` field to filter duplicates. In this way, you can avoid double-counting records when duplicate tokens are uploaded by different content managers.

## See Also

### Request and Response

object VppClientConfigRequest

The request for the client configuration.

