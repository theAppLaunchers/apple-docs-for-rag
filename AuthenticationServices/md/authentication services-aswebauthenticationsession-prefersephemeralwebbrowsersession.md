

- Authentication Services
- ASWebAuthenticationSession
-  prefersEphemeralWebBrowserSession 

Instance Property

# prefersEphemeralWebBrowserSession

A Boolean value that indicates whether the session should ask the browser for a private authentication session.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+macOS 10.15+visionOS 1.0+watchOS 6.2+

``` source
var prefersEphemeralWebBrowserSession: Bool { get set }
```

## Mentioned in 

Authenticating a User Through a Web Service

## Discussion

Set prefersEphemeralWebBrowserSession to `true` to request that the browser doesn’t share cookies or other browsing data between the authentication session and the user’s normal browser session. Whether the request is honored depends on the user’s default web browser. Safari always honors the request.

The value of this property is `false` by default.

Set this property before you call start(). Otherwise it has no effect.

