

- DeviceCheck
-  Accessing and modifying per-device data 

Article

# Accessing and modifying per-device data

Use a token from your app to query and modify two per-device binary digits stored on an Apple server.

## Overview

After you use the DCDevice class to generate an ephemeral token that identifies a device, your server uses HTTP `POST` commands to send requests to the query and update endpoints. The HTTP header field in each request must contain the authentication key you receive from Apple in a JSON web token (JWT). To create this token, you can use the same steps you use to create a provider authentication token for Apple Push Notification service (APNs); for details, see Communicate with APNs using authentication tokens.

### Create the payload for a query request

To query the bits, you create a JSON payload that contains the fields listed in the table below.

| Field name | Type | Description | Required |
|----|----|----|----|
| `device_token` | String (must not contain line breaks) | Base 64–encoded representation of encrypted device information | Yes |
| `transaction_id` | String | Unique transaction identifier from the associated server | Yes |
| `timestamp` | Long | UTC timestamp from the associated server, in milliseconds since the Unix epoch | Yes |

Here’s an example of a payload included in a query request:

```
```

When your query request succeeds, you receive a response that contains the fields listed in the table below.

| Field name | Type | Description |
|----|----|----|
| `bit0` | Boolean | The value of the first bit |
| `bit1` | Boolean | The value of the second bit |
| `last_update_time` | String | The date of the last modification, in YYYY-MM format |

### Create the payload for an update request

To update the bits, you create a JSON payload that contains the fields listed in the table below.

| Field name | Type | Description | Required |
|----|----|----|----|
| `device_token` | String (must not contain line breaks) | Base 64–encoded representation of encrypted device information | Yes |
| `transaction_id` | String | Unique transaction identifier from the associated server | Yes |
| `timestamp` | Long | UTC timestamp from the associated server, in milliseconds since the Unix epoch | Yes |
| `bit0` | Boolean | Value to set for the first bit | No |
| `bit1` | Boolean | Value to set for the second bit | No |

Here’s an example of a payload included in an update request:

```
```

If the update was successful, you receive the HTTP response code `200`. For a full list of the response codes you can receive, see Understand the HTTP response codes.

### Create the payload for a device validation request

To validate a device, you create a JSON payload that contains the fields listed in the table below.

| Field name | Type | Description | Required |
|----|----|----|----|
| `device_token` | String (must not contain line breaks) | Base 64–encoded representation of encrypted device information | Yes |
| `transaction_id` | String | Unique transaction identifier from the associated server | Yes |
| `timestamp` | Long | UTC timestamp from the associated server, in milliseconds since the Unix epoch | Yes |

Here’s an example of a payload included in a device-validation request:

```
```

If the request was successful, you receive the HTTP response code `200`. For a full list of response codes you can receive, see Understand the HTTP response codes.

### Send the request

Each request you send to the query and update endpoints must include an authorization header that contains your authentication key. The authentication key must use the ES256 algorithm and be in the Base 64 URL–encoded JSON web token format. If your token doesn’t use this format, you receive a `BAD_AUTHENTICATION_TOKEN` HTTP error.

In the `curl` command you create to send a request, you specify the authorization header and include your authentication key using `Bearer \`, like this:

``` -H "``Authorization: Bearer ``" \ ```

Important

Use the base URL shown in the example `curl` commands—that is, `https://api.development.devicecheck.apple.com`—only for testing during development. When you’re ready to transition to a production environment, you must use the production base URL `https://api.devicecheck.apple.com`.

To send a query request, your `curl` command might look similar to the one shown here:

```
```

To send an update request, your `curl` command might look similar to the one shown here:

```
```

To send a device-validation request, your `curl` command might look similar to the one shown here:

```
```

### Understand the HTTP response codes

When you use the query and update endpoints to communicate with the server, you may receive one of the response codes listed in the table below.

| Code | Descriptive string | Meaning |
|----|----|----|
| `200` | OK | The transaction was successful |
| `200` | Bit State Not Found | The bit state wasn’t found |
| `400` | Bad Device Token | The device token is missing or badly formatted |
| `400` | Bad Bits | The bits are missing or badly formatted |
| `400` | Bad Timestamp | The timestamp is missing or badly formatted |
| `400` | Bad Authorization Token | The authentication token is missing or badly formatted |
| `400` | Bad Payload | The payload is missing or badly formatted |
| `401` | Invalid Authorization Token | The authentication token can’t be verified |
| `401` | Authorization Token Expired | The authentication token has expired |
| `403` | Forbidden | The specified action isn’t allowed |
| `405` | Method Not Allowed | The endpoint was used incorrectly |
| `429` | Too Many Requests | Too many requests were sent to the server |
| `500` | Server Error | An error occurred on the server |
| `503` | Service Unavailable | The service is unavailable |

## See Also

### Device identification

class DCDevice

A representation of a device that provides a unique, authenticated token.

