

- Device Management
- App and Book Management
- Apps and Books for Organizations
-  Generating developer tokens 

Article

# Generating developer tokens

Create a JSON Web Token to authorize your requests to the Apps and Books for Organizations API.

## Overview

The header of every Apps and Books for Organizations API request requires authorization in the form of a developer token. A developer token is a signed token that authenticates you as a trusted developer and member of the Apple Developer Program.

### Construct your developer token

The Apps and Books for Organizations API supports the JSON Web Token (JWT) specification, so you can pass statements and metadata called *claims*. For more information, see the JWT specification and the available libraries for generating signed JWTs.

Use your developer account to create a Services identifier and obtain a key ID and to locate your Team ID.

Construct a developer token as a JSON object whose header contains:

`alg`  
The algorithm you use to sign the token, which must have a value of `ES256.`

`kid`  
A 10-character key ID obtained from your developer account.

Important

Apps and Books for Organizations supports only developer tokens signed with the ES256 algorithm. Apps and Books for Organizations rejects unsecured developer tokens or developer tokens signed with other algorithms. These rejections result in a `401` error code.

In the *claims* payload of the token, include:

`iss`  
The *issuer* registered claim key, a 10-character Team ID obtained from your developer account.

`iat`  
The *issued at* registered claim key, which indicates the time at which the token was generated, in terms of the number of seconds since epoch, in UTC.

`exp`  
The *expiration time* registered claim key, whose value must not be greater than `15777000` (6 months in seconds) from the current UNIX time on the server.

`origin`  
(Optional) The *origin* claim, recommended for web clients. Only use this JWT if the origin header of the request matches one of the values in the array. This addition helps prevent unauthorized use of the tokens. For example: “`origin`”`:[`”`https://example.com`”`,`”`https://music.example.com`”`]`.

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

### Authorize requests

If you manage request authorization directly, in all requests, pass the `Authorization: Bearer` header set to the developer token.

```
curl -v -H 'Authorization: Bearer [developer token]' "https://api.ent.apple.com/v1/test"
```

For more information about requests, responses, and error handling, see Handling requests and responses.

### Limit request rate

The Apps and Books for Organizations API limits the number of requests your app can make using a developer token within a specific period of time. If you exceed this limit, you’ll temporarily receive `429 Too Many Requests` error responses for requests that use the token. This error resolves itself shortly after the request rate has reduced.

## See Also

### Essentials

Handling requests and responses

Write a request for app or book metadata and handle responses from the API.

Fetching resources with extended attributes

Specify additional attributes for the API to include in a response.

Fetching storefront objects

Pick a region-specific geographic location to retrieve catalog information from.

Common Objects

Understand the common JSON objects that framework responses contain.

