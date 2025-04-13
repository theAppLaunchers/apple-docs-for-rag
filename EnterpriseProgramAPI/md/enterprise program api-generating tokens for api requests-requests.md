

- Enterprise Program API
-  Generating Tokens for API Requests 

Article

# Generating Tokens for API Requests

Create JSON Web Tokens (JWTs) signed with your private key to authorize API requests.

## Overview

JSON Web Token (JWT) is an open standard (RFC 7519) that defines a way to securely transmit information. The the Enterprise Program API requires JWTs to authorize each API request. You create the token, and sign it with the private key you downloaded from the Enterprise Program API.

To generate a signed JWT:

1.  Create the JWT header.

2.  Create the JWT payload.

3.  Sign the JWT.

Include the signed JWT in the authorization header of each the Enterprise Program API request.

### Create the JWT Header

To create a JWT to communicate with the the Enterprise Program API, use the following fields and values in the header:

| Header Field | Value |
|----|----|
| `alg` - Encryption Algorithm | `ES256`  All JWTs for the Enterprise Program API must be signed with ES256 encryption. |
| `kid` - Key Identifier | Your private key ID from the Enterprise Program API, for example, `2X9R4HXF34` |
| `typ` - Token Type | `JWT` |

To get your key ID for you API key for the Enterprise Program API, log in to the Apple Developer website and:

1.  Select Users and Access.

2.  Select the Integrations tab.

The key IDs appear in a column under the Active heading.

1.  Hover the cursor next to a key ID to display the Copy Key ID link.

2.  Click Copy Key ID.

Tip

If you have more than one Enterprise Program key, use the key ID of the same private key that you use to sign the JWT.

Here’s an example of a JWT header:

```
```

### Create the JWT Payload for Enterprise Program API Keys

The JWT payload contains information specific to the the Enterprise Program APIs, such as issuer ID and expiration time. Use the following fields and values in the JWT payload:

| **Payload Field** | **Value** |
|----|----|
| `iss` - Issuer ID | Your issuer ID from the Integrations page in the the Apple Developer website, for example, `57246542-96fe-1a63-e053-0824d011072a` |
| `iat` - Issued At Time | The token’s creation time, in UNIX epoch time, for example, `1528407600` |
| `exp` - Expiration Time | The token’s expiration time in Unix epoch time. Tokens that expire more than 20 minutes into the future are not valid except for resources listed in Determine the Appropriate Token Lifetime. |
| `aud` - Audience | `apple-developer-enterprise-v1` |
| `scope` - Token Scope | A list of operations you want the Enterprise Program API to allow for this token; for example, `GET /v1/users/123` (Optional) |

To get your issuer ID, log in to the Apple Developer website and:

1.  Select Users and Access.

2.  Select the Integrations tab.

The issuer ID appears near the top of the page. To copy the issuer ID, click Copy next to the ID.

Here’s an example of a JWT payload:

```
```

### Determine the Scope of the Token

To reduce potential attack surface and improve security of your tokens, you can explicitly specify the scope of a token. The scope tells the Enterprise Program API which requests it needs to accept for the token. If you unintentionally share a token with an unauthorized party, a limited scope reduces the requests that a potential attacker can make using the token.

The scope claim is an array of strings, each representing a request. Each scope entry includes:

- The HTTP `GET` method

- The URL path, for example, `/v1/users` or `/v1/bundleIds/1234`

- The optional URL query string, for example, `?filter[platform]=IOS`

the Enterprise Program API rejects a token with a scope claim if none of the scope entries match the attempted request.

Note

The order of query parameters isn’t important. Additionally, the Enterprise Program API ignores the following query parameters when it checks the scope: `limit`, `cursor`, and `sort`.

The following code listing shows an example of a JWT payload with a scope.

```
```

With this payload, the Enterprise Program API only allows you to fetch a list of bundle IDs for iOS using the List Bundle Ids endpoint if you use the `filter[platform]=IOS` query parameter.

You can use a JWT without a `scope` for any request as long as the role of the API key allows it.

### Determine the Appropriate Token Lifetime

For every request, the Enterprise Program API calculates the valid time for a token, referred as the token’s `lifetime`, by subtracting the `iat` claim from the `exp` claim. For increased security, carefully consider the lifetime of tokens you create and choose a lifetime that doesn’t allow usage of the token for longer than necessary. For example, an appropriate lifetime for a token you use for a one-off request is two minutes. In contrast, consider using a token with a lifetime of 20 minutes for a long-running process that makes many requests with the same token. Additionally, consider generating a new token periodically throughout the process, instead of issuing tokens with longer lifetimes.

For most requests, the Enterprise Program API rejects a token with a lifetime greater than 20 minutes.

### Sign the JWT

Use the private key associated with the key ID you specified in the header to sign the token.

Regardless of the programming language you’re using with the the Enterprise Program API, there are a variety of open source libraries available online for creating and signing JWT tokens. See JWT.io for more information.

Tip

You don’t need to generate a new token for every API request. To get better performance from the the Enterprise Program API, reuse the same signed token for multiple requests until it expires.

### Include the JWT in the Request’s Authorization Header

Once you have a complete and signed token, provide the token in the request’s authorization header as a bearer token.

The following example shows a `curl` command using a bearer token. Replace the text `[signed token]` with the value of the signed token itself.

```
curl -v -H 'Authorization: Bearer [signed token]' 
"https://api.enterprise.developer.apple.com/v1/certificates"
```

## See Also

### Essentials

Creating API Keys for Enterprise Program API

Create API keys to sign JSON Web Tokens (JWTs) and authorize API requests.

Revoking API Keys

Revoke unused, lost, or compromised private keys.

Identifying Rate Limits

Recognize the rate limits that REST API responses provide and handle them in your code.

Enterprise Program API Release Notes

Learn about new features and updates in the Enterprise Program API.

