

- WeatherKit REST API
-  Request authentication for WeatherKit REST API 

Article

# Request authentication for WeatherKit REST API

Create a developer token to access weather data.

## Overview

To make requests to the WeatherKit REST API, authorize yourself as a trusted developer and member of the Apple Developer Program (ADP). The header of every WeatherKit REST API request requires a signed developer token to identify the authorized ADP member and application or service making the request.

### Create a private key and Service ID

Create a WeatherKit identifier and private key so you can use a developer token to authenticate yourself as a trusted developer and member of the Apple Developer Program.

To begin, go to your Apple Developer Account, then navigate to Certificates, Identifiers & Profiles. Select the Keys menu to create and download a WeatherKit key.

Next, create a Service ID from the Identifiers menu.

- Click + to add, select Services IDs, and then Continue.

- Set a description and the identifier you wish to use, for example, `com.example.weatherkit-client`.

- Click Continue, then Register to register the identifier.

### Generate the web token

WeatherKit supports the JSON Web Token (JWT) specification, and allows you to pass statements and metadata called claims. For more information about JWT, see the JWT specification. There are a variety of open source libraries available online for creating and signing JWT tokens. See JWT.io for more information.

Construct a developer token as a JSON object with a header that contains the following information:

`alg`  
The algorithm with which to sign the token. Set the value to `ES256`.

`kid`  
A 10-character key identifier you obtain from your developer account.

`id`  
An identifier that consists of your 10-character Team ID and Service ID, separated by a period.

WeatherKit only supports developer tokens signed with the ES256 algorithm, and rejects unsecured developer tokens or developer tokens signed with other algorithms. These rejections result in a 401 error code.

Note

Ensure that the token contains only the claims listed below.

In the claims payload of the token, include the following:

`iss`  
The issuer claim key. This value is your 10-character Team ID from your developer account.

`iat`  
The issued-at claim key. This value indicates the time at which the token was generated. The value is the number of seconds since epoch in Universal Coordinated Time.

`exp`  
The expiration time claim key. This value indicates the time after which the token is not accepted by the server. The value is the number of seconds since epoch in Universal Coordinated Time.

`sub`  
The subject public claim key. This value is your registered Service ID.

A decoded developer token has the following format:

```
```

After you create the token, sign it with your WeatherKit private key using the ES256 algorithm, which is the JSON Web Algorithms (JWA) name for the Elliptic Curve Digital Signature Algorithm (ECDSA) with the P-256 curve and the SHA-256 hash.

Follow these guidelines whenever you use signed JWTs:

- Never distribute your private key. If you need to create tokens for apps or websites, create an authenticated service to create and sign your own tokens.

- Be mindful of token expiration times. Longer times require less overhead, but shorter times ensure a higher level of security.

- If your token has an extended time before expiring, be sure to store it securely.

### Authorize requests

Pass the developer token as a parameter to the `Authorization: Bearer` header in each request. Here’s an example of a request:

```
```

