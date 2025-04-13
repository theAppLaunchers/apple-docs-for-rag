

- Apple Music Feed
-  Generating developer tokens 

Article

# Generating developer tokens

Create a JSON Web Token to authorize your requests to Apple Media Feed API.

## Overview

The header of each Apple Media Feed API request requires authorization in the form of a developer token. A developer token is a signed token that authenticates you as a trusted developer and member of the Apple Developer Program.

Apple Media Feed API limits the number of requests you can make using a developer token within a specific period of time. If you exceed this limit, you temporarily receive `429 Too Many Requests` error responses for requests that use the token. This error resolves itself shortly after the request rate reduces.

## Create your developer token

Configuring a media identifier and authorization key using your developer account allows you to obtain a key ID to use in your developer token.

Apple Media Feed API supports the JSON Web Token (JWT) specification, so you can pass statements and metadata called *claims*. For more information, see the JWT specification and the available libraries for generating signed JWTs.

Create a developer token as a JSON object with a header that includes the following:

`alg`  
The algorithm you use to sign the token, which requires the value of `ES256`.

`kid`  
A 10-character key ID that you obtain from your developer account.

Important

Apple Media Feed API supports only developer tokens signed with the ES256 algorithm. Unsecured developer tokens or developer tokens signed with other algorithms reject with a `401` error code.

In the claims payload of the token, include the following:

`iss`  
The *issuer* registered claim key, a 10-character Team ID from your developer account.

`iat`  
The *issued at* registered claim key. This value indicates the time that the system generated the token, in UNIX time.

`exp`  
The *expiration time* registered claim key. This value can’t be greater than `15777000` (6 months in seconds) from the current UNIX time on the server.

`origin`  
(Optional) The *origin* claim, recommended for web clients. Only use this JWT if the origin header of the request matches one of the values in the array. This addition helps prevent unauthorized use of the tokens. For example: `“origin“:[“https://example.com“,“https://music.example.com“]`.

Tip

To locate your Team ID, sign in to your developer account, and click “Membership details” at the top of the page.

A decoded developer token has the following format:

```
{
     "alg": "ES256",
     "kid": "ABC123DEFG"
}
{
     "iss": "DEF123GHIJ",
     "iat": 1437179036,
     "exp": 1493298100
}
```

After you create the token, sign it with your private key using the ES256 algorithm.

Note

ES256 is the JSON Web Algorithms (JWA) name for the Elliptic Curve Digital Signature Algorithm (ECDSA) with the P-256 curve and the SHA-256 hash.

## Authorize requests

If you manage request authorization directly, in all requests, pass the `Authorization: Bearer` header set to the developer token.

```
curl -v -H 'Authorization: Bearer [developer token]' "https://api.ent.apple.com/v1/test"
```

## See Also

### Essentials

Requesting a feed export

Create requests for Apple Music Catalog metadata.

Interpreting responses

Learn about responses from Apple Media Feed API to your Apple Music Feed requests.

