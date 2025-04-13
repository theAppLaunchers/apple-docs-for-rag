

- Device Management
- User Enrollment
- Onboarding users with account sign-in
-  Implementing the OAuth2 authentication user-enrollment flow 

Article

# Implementing the OAuth2 authentication user-enrollment flow

Understand the steps of the OAuth2 flow between the user, client, server, and Apple services.

## Overview

To implement user enrollment, you must support a series of interactions between the user’s device and your MDM server. The diagrams below illustrates the interactions with the text describing the interactions in more detail.

To implement the OAuth2 flow, steps 1-4 are identical to the simple flow explained in Implementing the simple authentication user-enrollment flow.

### 401 response

In step 5 above, the server returns an `HTTP 401` response status to the client and includes a `WWW-Authenticate` response header. This response header must use the `Bearer` scheme and include the following parameters:

| Name | Content |
|----|----|
| `method` | (Required) A string that must be `apple-oauth2`, defining the authentication protocol. |
| `authorization-url` | (Required) The OAuth2 protocol authorization endpoint URL, for the initial ASWebAuthenticationSession HTTP request. The URL scheme must be `https`. |
| `token-url` | (Required) The OAuth2 protocol token endpoint URL, for the token request. The URL scheme must be `https`. |
| `redirect-url` | (Required) The OAuth2 protocol redirection endpoint URL, where the OAuth2 authorization request redirects to on success. Since the authorization request uses the ASWebAuthenticationSession protocol, this URL scheme must be set to `apple-remotemanagement-user-login` and have a path component set to the server’s redirection endpoint. |
| `client-id` | (Required) The OAuth2 protocol client identifier that the client must use in the OAuth2 authorization request. |
| `scope` | The OAuth2 protocol access token scope the client must use in the OAuth2 authorization request. |

If the client’s enrollment request is invalid, the server returns a standard HTTP error response code (for example, 400 or 403) to halt the enrollment flow on the device. If the server’s response is invalid (for example, missing the `WWW-Authenticate` response header), then the system cancels the enrollment.

### Authorization request

In steps 6-10 above, the client starts the OAuth2 authorization grant flow by constructing the authorization request URL from the parameters returned in the 401 response, and adds a query item with the name `login_hint`, with its value set to the user account identifier entered by the user.

The client creates an ASWebAuthenticationSession using the authorization request URL and a callback scheme set to `apple-remotemanagement-user-login`, and starts the session.

The authentication session does an `HTTPS GET` request for the OAuth2 authorization request URL, and includes the appropriate query parameters needed for the authorization code grant request. The device presents any resulting HTML data to the user in a web view.

The OAuth2 authorization server responding to the request can pre-populate any user id form field by extracting the relevant items from the request’s `login_hint` query item. The server can also use that query item to customize the form based on the user name or domain portions of the user account identifier.

ASWebAuthenticationSession supports most types of browser based single sign-on, multi-factor, or federated authentication. There can be several round trips between the client and the authorization server to complete authentication.

The user does have the option of canceling out of the web-view at any time, and that terminates the authentication flow and the enrollment.

```
>>>> Response
HTTP/1.1 200 OK
Content-Type: text/html; charset="utf-8"
Content-Length: 17643

…

```

### Authorization response

In step 11 above, the authentication session web flow completes when the server returns an HTTP 308 permanent redirect response to the client, with a `Location` header set to the `redirect-url` parameter value returned in step 5. The URL must also include the OAuth2 protocol `code` and `state` query items (note the client always sets a `state` parameter in its authorization request, so the server must always set it in the authorization response).

```
>>>> Response
HTTP/1.1 308 Permanent Redirect
Content-Length: 0
Location: apple-remotemanagement-user-login:/oauth2/redirection
    ?code=Dek1jUOEcaIPGhbDrCTm9GDV5qT1sb&state=340B948D-A84A-45A3-AC45-C93195124B00
```

### Token request and response

In steps 12-13 above, the client then makes a token access request to fetch the OAuth2 access and (optional) refresh tokens, using the authorization grant code returned in step 11, along with other required OAuth2 parameters. The client securely stores the tokens returned by the server for use when authorizing subsequent requests to the server.

If authentication fails, the server should return an appropriate HTTP error response code that terminates the enrollment on the device.

```
>>>> Response
HTTP/1.1 200 OK
Content-Length: 245
Content-Type: application/json

{
    "token_type": "Bearer",
    "scope": "MDM",
    "access_token": "dXNlcm9hdXRo.MjZkNTkzZmMtNzk4MC00OWFkLTllZTAtZTA2NzhmNmVhNzg5",
    "expires_in": 3600,
    "refresh_token": "dXNlcm9hdXRo.NzhiNWU0NWQtMDVlZS00MTAwLThhMjEtZDA5MzI2N2RjNzUx"
}
```

### Second enrollment attempt to enrollment

In steps 14-21 above, the behavior is identical to the second enrollment attempt from the simple authentication protocol, with the client using the OAuth2 access token value in the `Authorization` HTTP request header.

```
Authorization: Bearer dXNlcm9hdXRo.MjZkNTkzZmMtNzk4MC00OWFkLTllZTAtZTA2NzhmNmVhNzg5
```

## See Also

### Detailed flow instructions

Implementing the simple authentication user-enrollment flow

Understand the steps of the authentication flow between the user, client, server, and Apple services.

