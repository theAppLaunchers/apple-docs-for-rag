

- MarketplaceKit
-  Installing your app from your website 

Article

# Installing your app from your website

Manage the installation of an app that you develop and distribute through your website.

## Overview

Alternative distribution apps approved for download from your website install when people navigate to a special URL scheme; see Distributing your app from your website.

When someone taps a button mapped to the URL, the system makes several requests of your web server to facilitate the installation. Each of the following services that you implement on your web server contain at least two endpoints:

- Authentication server

- Licensing server

- App-data server

MarketplaceKit supports authentication through the the OAuth 2.0 specification IETF RFC 6749. If your website requires someone to be signed-in before they can download an app, or to have made a purchase, include an authentication token in the MarketplaceKitURIScheme URL to begin the authorization process.

After your server authorizes the device, the system requests a license for the app. Your server uses App License Delivery SDK in conjunction with the encryption and signing assets that Apple provides to implement *digital rights management* by issuing a dynamic license for each installation of an app.

After the device receives a license, the system requests the app data from your web server’s `restore` endpoint to install the app.

## Authenticate the page visitor

To restrict download access to a specific set of people, include a token in the `MarketplaceKitURIScheme` request. If you include the optional `token` parameter in the URL, MarketplaceKit passes the value to your athentication server to begin authorization. The system looks for details about your authentication server at the following URL:

```
/.well-known/oauth-authorization-server
```

At this URL, host a JSON file with the following configuration:

```
{
    "authorization_endpoint": 
        "/oauth/authorize",
    "code_challenge_methods_supported": [
        "5256"
    ],
    "grant_types_supported": [
        "authorization_code"
    ],
    "issuer": "",
    "response_types_supported": [
        "code",
        "token"
    ],
    "token_endpoint": "/oauth/token"
}
```

Important

Host the file using `https://` with a valid certificate. Don’t use redirects. For more information, see Supporting associated domains.

The system sends the token from your download URL in a POST to your `token_endpoint` in the format of described in RFC 8693 section 2.3, for example:

```
POST /oauth/token HTTP/1.1
Host: server.example.com
Content-Type: application/x-www-form-urlencoded

grant_type=urn:ietf:params:oauth:grant-type:token-exchange
&issued_token_type=urn:ietf:params:oauth:token-type:access_token
&subject_token=eyJhbGciOiJSUzI1NiIsImtpZCI6IjIyIn0
&subject_token_type=urn:ietf:params:oauth:token-type:access_token
&client_id=6ef01a168f14431d98a0626cf5c89104
```

The fields in the POST body are:

| URL parameter | Description |
|----|----|
| `grant_type` | The grant type, `urn:ietf:params:oauth:grant-type:token-exchange`, per RFC 8693. |
| `issued_token_type` | The token type, `ietf:params:oauth:token-type:access_token`. |
| `client_id` | A value that’s unique for each device, website domain, and account. The system generates a new value if it doesn’t already exist, which might occur after someone deletes the app. The value might change until the person approves the app developer in Settings. |
| `subject_token` | The `token` in the MarketplaceKitURIScheme request. |
| `subject_token_type` | The subject token type, `ietf:params:oauth:token-type:access_token`. |

Important

`client_id` isn’t a stable way to identify a customer or track the number of simultaneous installs of an app for an account. To identify the customer, use the `token` parameter in the MarketplaceKitURIScheme instead. To track installation counts for an app, see Licensing alternative distribution apps.

Your token endpoint responds to the request with an access token and, optionally, a refresh token. Here’s an example response:

```
HTTP/1.1 200 OK
Content-Type: application/json;charset=UTF-8
Cache-Control: no-store
Pragma: no-cache

{
   "access_token": "2YotnFZFEjr1zCsicMWpAA",
   "refresh_token": "82u9fehjiofasbkr3290",
   "token_type": "bearer",
   "expires_in": 3600
}
```

| URL parameter | Description |
|----|----|
| `access_token` | A token that authorizes the system to manage apps on behalf of the page visitor. |
| `refresh_token` | An optional token that the system exchanges for another access token after the original access token expires. |
| `token_type` | The value `"bearer"` (required). |
| `expires_in` | The time, in seconds, during which the system considers the token valid. |

When the system makes subsequent calls to your web server for app licenses, app installs (*restores*), or app updates, it includes the bearer token in the header for your server to validate the communication and associate with the person’s account.

Note

For more information on implementing an authentication service, such as generating the tokens, refer to OAuth 2.0 Authorization Framework Specification, IETF RFC 6749. All communication between your server and device needs to occur over TLS.

## Retrieve a license for the app from your web server

If your website doesn’t require authentication or the device is already successfully authorized to act on behalf of the page visitor, the system requests an app license from your web server. To process license requests, your web server implements an endpoint that serves generated licenses by using App License Delivery SDK.

## Serve a restore request

When your server responds with a license, the system requests to download your app. Your web server needs to provide a JSON file at the following URL:

```
/.well-known/marketplace-kit
```

Inside the file, define an endpoint to handle `restore` requests from the device:

```
"restore": "/PATH",
```

The system calls your restore endpoint with the following example POST:

```
{ 
    "apps": [
       { 
          "appleItemId": "",
          "appleVersionId" : ""
       }
    ], 
    "platform" : "iOS",
    "osVersion" : "17.4"
}
```

The request contains the following fields:

| Request field | description |
|----|----|
| `apps` | An array that contains an object for each app in the request. Each object in the array consists of an identifier (AppleItemID) and version (AppleVersionID) for the requested app. |
| `platform` | A string that identifies the platform of the installing device. |
| `osVersion` | A string that identifies the operating system version of the installing device. |

Compare the `platform` and `osVersion` fields to those contained within the app’s manifest to confirm that your alternative distribution package supports the device attempting to install it.

If downloading your app requires authorization and the system communicates with your endpoint without a valid access token, request reauthentication in your response. An invalid access token can result from token expiration, or the restoration of a device from a backup. For more information, see Reauthenticating a person to manage apps.

Otherwise, send your app in response by supplying a URL in the `restores` element to the alternative distribution package for the requested app version:

```
{
    "restores": [
        {
            "appleItemId": "10737747186",
            "appleVersionId": "2000004563",
            "alternativeDistributionPackage": 
                "/PATH",
            "installVerificationToken" : ""
            "appShareURL" : 
        }
    ]
}
```

The `"restores"` array in the response contains an object with the following fields:

| Response field | description |
|----|----|
| `appleItemId` | An identifier for your app. For more information, see AppleItemID. |
| `appleVersionId` | A version number that corresponds to the alternative distribution package. For more information, see AppleVersionID. |
| `alternativeDistributionPackage` | Your app’s alternative distribution package in the assembled format described in Ingesting an alternative distribution package. This value has unique domain-matching requirements; for more information, see MarketplaceKitURIScheme. |
| `installVerificationToken` | A JSON web signature that MarketplaceKit uses for installations. For more information, see Supplying an install verification token. |
| `appShareURL` | A URL to a product landing page for the app on your marketplace website. The operating system populates the value in the Share Sheet when a person touches and holds the app’s icon on the Home Screen. |

## See Also

### Web services

Processing alternative app marketplace notifications

Manage the addition and removal of apps available on your alternative marketplace.

Ingesting an alternative distribution package

Process an available app version from App Store Connect and store it for download from your server.

Installing apps from an alternative marketplace

Manage the installation of apps that developers distribute from your marketplace app.

Supplying an install verification token

Support the installation of alternative distribution apps by creating signed JSON web tokens.

