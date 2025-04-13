

- Exposure Notification
-  Changing Configuration Values Using the Server‑to‑Server API 

Article

# Changing Configuration Values Using the Server‑to‑Server API

Update Exposure Notifications configuration values from a Public Health Authority’s server.

## Overview

The Exposure Notifications feature reads configuration values to customize behavior for each region based on values provided by that region’s Public Health Authority (PHA). PHAs can push changes to these configuration values from their servers using the Exposure Notifications server-to-server API. A PHA might use the server-to-server API, for example, to automate changes under certain conditions, such as changing the polling interval when experiencing unusually high activity, or providing a configuration portal hosted on their own servers.

Exposure Notifications server-to-server API is located at the following URL:

```
```

This API expects a POST request with a content-type of `application/json.` Requests must include both of the custom headers listed below to authenticate the request. The server rejects requests that the API can’t authenticate, and doesn’t make any changes to the existing configuration values.

`X-Apple-verification-data`  
The name of the Health Authority submitting the request as a Base64-encoded UTF-8 string.

`X-Apple-signature`  
A digital signature of the string in the `X-Apple-verification-data` header, signed with the private key that corresponds to the most recent public key provided to Apple.

The body of the POST request contains a JSON dictionary that uses the following keys:

`appBundleID`  
Identifier for the client app to which these configuration changes apply. This field isn’t needed when making changes that only apply to Exposure Notifications Express.

`countryCode`  
The two-letter ISO country code that corresponds to the region for which these configuration changes apply.

`state`  
The two-letter subdivision code that corresponds to the state, province, or other administrative division for which these configuration changes apply, if needed.

`publicKeyVersion`  
An integer that represents the version of the PHA’s public key, for use when authenticating requests using the custom headers, listed above.

`config`  
A JSON dictionary used to specify new configuration values. For a list of available keys and their expected values, see Configuring Exposure Notifications.

This API responds with an HTTP response code, but won’t send a response body or any custom headers. If the API can make the requested changes, the API returns an HTTP `200` response code. If the API can’t change the values, it returns one of the following codes:

`400` (Invalid Payload)  
Can’t validate the JSON in the body of the request. This could be because the JSON is invalid, missing required keys, or includes unrecognized keys.

`401` (Unauthorized)  
Can’t validate the PHA’s digital signature contained in the custom headers.

`404` (Not Found)  
Can’t find a configuration for the country and state (or subdivision) specified in the request JSON.

`500` (Internal Server Error)  
Encountered some other error. This response code doesn’t necessarily indicate a problem with the request.

## See Also

### Essentials

Supporting Exposure Notifications Express

Configure servers to notify users of potential exposures to COVID-19 without an app.

Building an App to Notify Users of COVID-19 Exposure

Inform people when they may have been exposed to COVID-19.

Setting Up a Key Server

Ensure that your server meets the requirements for supporting Exposure Notifications.

class ENManager

A class that manages exposure notifications.

ENDeveloperRegion

A string that specifies the region that the app supports.

ENAPIVersion

A number that specifies the version of the API to use.

Testing Exposure Notifications Apps in iOS 13.7 and Later

Perform end-to-end validation of Exposure Notifications apps on a device by manually loading configuration files.

Supporting Exposure Notifications in iOS 12.5

Prepare your Exposure Notifications app to run on a previous version of iOS.

