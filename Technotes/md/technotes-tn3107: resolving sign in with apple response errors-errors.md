

- Technotes
-  TN3107: Resolving Sign in with Apple response errors 

Article

# TN3107: Resolving Sign in with Apple response errors

Diagnose errors received by the Sign in with Apple client, or its server infrastructure, by identifying the underlying causes of common error codes and explore their potential solutions.

## Overview

This document aids in debugging response errors relating to Sign in with Apple. This information supplements the Sign in with Apple documentation — including Sign in with Apple REST API, Sign in with Apple JS SDK, as well as the Authentication Services framework — so start with the documentation first to ensure the client is using the APIs properly.

## Authorization response errors

Errors can occur during Sign in with Apple authorization requests — such as when the client asks permission for the user’s information after a successful Apple ID authentication. For example, the provided client ID is invalid or unauthorized, the request parameters are incorrect, or the redirect URI is invalid or misconfigured for the web service. When errors occur, the authorizing server sends a standard OAuth error response with an error code.

The following example shows a sample error response in JSON format received from the `/auth/authorize` endpoint:

```
HTTP/1.1 400 Bad Request
Content-Type: application/json;charset=UTF-8
Cache-Control: no-store
Pragma: no-cache

{
  "error": "invalid_request"
}
```

To help troubleshoot why an authorization error occurred, review the following error code descriptions:

| Error Code | Description | Solution |
|----|----|----|
| `invalid_request` | The authorization request is missing a required parameter, includes an invalid parameter value, includes a parameter more than once, or is otherwise malformed. | Check that all parameters are correct, the provided `client_id` exists and is identical to the value registered to your developer account (case-sensitive), etc. |
| `invalid_client` | The authorization request is invalid because the primary app or web service with the provided `client_id` could not be found. | Check that all parameters are correct, the provided `client_id` exists and is identical to the value registered to your developer account (case-sensitive), etc. |
| `unauthorized_client` | The client is not authorized to request an authorization code using this method: The `redirect_uri` of the service either is incorrect or not provided. | Make sure the provided `redirect_uri` is valid, publicly accessible, and is identical to the value registered for the service. |
| `invalid_scope` | The requested `scope` is invalid. | Make sure the request is correct, and that the provided `scope` is supported, etc. |

For more information about OAuth error responses, see RFC 6749.

## Token response errors

Errors can occur during Sign in with Apple token requests — such as token generation when creating transfer identifiers and exchanging transfer identifiers during user migration, or token validation for a user’s credentials. For example, the provided token is invalid or expired, the client secret — a JSON Web Token (JWT) — is invalid or expired, or the request parameters are incorrect, malformed, or not percent-encoded. When errors occur, the token validation server sends a standard OAuth error response with an error code.

The following example shows a sample error response in JSON format received from the `/auth/token` endpoint:

```
HTTP/1.1 400 Bad Request
Content-Type: application/json;charset=UTF-8
Cache-Control: no-store
Pragma: no-cache

{
  "error": "invalid_client"
}
```

To help troubleshoot why a token generation or validation error occurred, review the following error code descriptions:

| Error Code | Description | Solution |
|----|----|----|
| `invalid_request` | The token request is missing a required parameter, includes an invalid header or parameter value, includes a parameter more than once, or is otherwise malformed. | Check that the content type is valid, all parameters are correct, the form data is percent-encoded, etc. See Possible Reasons for Invalid Request Errors below for details. |
| `invalid_client` | The token request is invalid because the `client_secret` is invalid or expired, is improperly signed, or is otherwise malformed. | Check that all parameters are correct, the form data is percent-encoded, the JWT header and claim values are correct and the signature is valid, etc. See Possible Reasons for Invalid Client Errors below for details. |
| `invalid_grant` | The client is not authorized for the provided `code` or `refresh_token`, or the `code` or `refresh_token` is invalid, previously consumed, or expired. | Check that all parameters are correct, the provided token is valid, etc. See Possible Reasons for Invalid Grant Errors below for details. |

For more information about JWTs and their errors, see RFC 7519 and RFC 7523.

## Revoke response errors

Errors can occur during Sign in with Apple revoke requests — such as token revocation after a user account deletion. For example, the provided token does not match the token type hint, the client secret — a JSON Web Token (JWT) — is invalid or expired, or the request parameters are incorrect, malformed, or not percent-encoded. When errors occur, the token revocation server sends a standard OAuth error response with an error code.

The following example shows a sample error response in JSON format received from the `/auth/revoke` endpoint:

```
HTTP/1.1 400 Bad Request
Content-Type: application/json;charset=UTF-8
Cache-Control: no-store
Pragma: no-cache

{
  "error": "invalid_client"
}
```

To help troubleshoot why a token generation or validation error occurred, review the following error code descriptions:

| Error Code | Description | Solution |
|----|----|----|
| `invalid_request` | The token request is missing a required parameter, includes an invalid header or parameter value, includes a parameter more than once, or is otherwise malformed. | Check that the content type is valid, all parameters are correct, the form data is percent-encoded, etc. See Possible Reasons for Invalid Request Errors below for details. |
| `invalid_client` | The token request is invalid because the `client_secret` is invalid or expired, is improperly signed, or is otherwise malformed. | Check that all parameters are correct, the form data is percent-encoded, the JWT header and claim values are correct and the signature is valid, etc. See Possible Reasons for Invalid Client Errors below for details. |
| `invalid_grant` | The client is not authorized for the provided `code` or `refresh_token`, or the `code` or `refresh_token` is invalid, previously consumed, or expired. | Check that all parameters are correct, the provided token is valid, etc. See Possible Reasons for Invalid Grant Errors below for details. |

For more information about JWTs and their errors, see RFC 7519 and RFC 7523.

## User migration info response errors

Errors can occur during Sign in with Apple user migration info requests — such as access token generation, transfer identifier generation, and exchanging transfer identifiers for team-scoped user credentials. For example, the provided access token is invalid or expired, the client secret is invalid or expired, the request parameters are incorrect, or the user has revoked access to the client. When errors occur, the user migration info server sends a standard OAuth error response with an error code.

The following example shows a sample error response in JSON format received from the `/auth/usermigrationinfo` endpoint:

```
HTTP/1.1 400 Bad Request
Content-Type: application/json;charset=UTF-8
Cache-Control: no-store
Pragma: no-cache

{
  "error": "invalid_request"
}
```

To help troubleshoot why a user migration token generation or validation error occurred, review the following error code descriptions:

| Error Code | Description | Solution |
|----|----|----|
| `invalid_request` | The user migration info request is missing a required parameter, includes an invalid header or parameter value, includes a parameter more than once, or is otherwise malformed. | Check that the content type is valid, all parameters are correct, the form data is percent-encoded, etc. See Possible Reasons for Invalid Request Errors below for details. |
| `invalid_client` | The user migration info request is invalid because the `client_secret` is invalid or expired, is improperly signed, or is otherwise malformed. | Check that all parameters are correct, the form data is percent-encoded, the JWT header and claim values are correct and the signature is valid, etc. See Possible Reasons for Invalid Client Errors below for details. |

For more information about OAuth error responses, see RFC 6749.

## Possible reasons for invalid request errors

An `invalid_request` error can occur during a Sign in with Apple request for several reasons, but most commonly for the following scenarios:

- The request has an invalid content type.

- The request is missing a required parameter.

- The request contains an unsupported parameter.

- The request includes multiple user credentials — a mismatched access token, `client_id`, and `client_secret` subject (`sub`) values, or duplicate parameters.

- The user has revoked authorization for the client.

## Possible reasons for invalid client errors

An `invalid_client` error can occur during a Sign in with Apple request for several reasons, but most commonly while providing client credentials for server validation:

- The request has form data that is not percent-encoded.

- The `client_secret` is missing required headers or payload claims.

- The `client_secret` has a `sub` claim that is not identical to the value registered to your developer account.

- The `client_secret` has expired.

- The `client_secret` signature is invalid or in an unsupported byte format.

To validate the `client_secret` and its signature, see JWT.io and RFC 7515. If you use a third-party library to create, verify, and sign the JWT, make sure the library meets the following criteria for Sign in with Apple:

- Supports `E256` digital signatures

- Supports the required headers and payload claims

- Does not decode using `ASN.1 DER` byte format

## Possible reasons for invalid grant errors

An `invalid_grant` error can occur during a Sign in with Apple request for several reasons, but most commonly for the following scenarios while performing token validation.

**For authorization code token validation requests:**

- The `client_id` does not match the client for which the `code` was issued.

- The `code` has expired or has been previously consumed by the validation server.

**For refresh token validation requests:**

- The `client_id` does not match the client for which the `refresh_token` was issued.

- The `refresh_token` is invalid or has expired.

## Revision History

- **2024-01-16** Updated content to include more underlying causes of response errors, and added token revoke endpoint.

- **2022-05-24** Made minor editorial changes.

- **2022-02-15** First published.

## See Also

### Latest

TN3182: Adding privacy tracking keys to your privacy manifest

Declare the tracking domains you use in your app or third-party SDK in a privacy manifest.

TN3183: Adding required reason API entries to your privacy manifest

Declare the APIs that can potentially fingerprint devices in your app or third-party SDK in a privacy manifest.

TN3184: Adding data collection details to your privacy manifest

Declare the data your app or third-party SDK collects in a privacy manifest.

TN3181: Debugging an invalid privacy manifest

Identify common configurations that cause unsuccessful privacy manifest validation with the App Store.

TN3180: Reverting to App Store Server Notifications V1

Migrate from version 2 to version 1 of App Store Server Notifications using the Modify an App endpoint.

TN3179: Understanding local network privacy

Learn how local network privacy affects your software.

TN3178: Checking for and resolving build UUID problems

Ensure that every Mach-O image has a UUID, and that every distinct Mach-O image has its own unique UUID.

TN3177: Understanding alternate audio track groups in movie files

Learn how alternate groups collect audio tracks, and how to choose which audio track to use in your app.

TN3111: iOS Wi-Fi API overview

Explore the various Wi-Fi APIs available on iOS and their expected use cases.

TN3176: Troubleshooting Apple Pay payment processing issues

Diagnose errors that occur when processing Apple Pay payments, identify common causes, and explore potential solutions.

TN3175: Diagnosing issues with displaying the Apple Pay button on your website

Diagnose common errors received while displaying the Apple Pay button on your website by identifying the underlying causes, and explore potential solutions.

TN3174: Diagnosing issues with the Apple Pay payment sheet on your website

Diagnose errors received while presenting the Apple Pay payment sheet on your website by identifying the underlying causes of common errors and explore their potential solutions.

TN3173: Troubleshooting issues with your Apple Pay merchant identifier configuration

Diagnose errors due to invalid Apple Pay merchant identifier configurations by identifying the underlying causes of common errors and explore their potential solutions.

TN3168: Making your App Clip available in the App Store

Learn how to configure your App Clip to prevent it from being unavailable in the App Store.

TN3124: Debugging coordinate space issues

Learn techniques to help debug any coordinate space issue.

