

- Foundation
- URLSessionTaskDelegate
-  urlSession(\_:task:didReceive:completionHandler:) 

Instance Method

# urlSession(\_:task:didReceive:completionHandler:)

Requests credentials from the delegate in response to an authentication request from the remote server.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+macOS 10.9+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
optional func urlSession(
    _ session: URLSession,
    task: URLSessionTask,
    didReceive challenge: URLAuthenticationChallenge,
    completionHandler: @escaping (URLSession.AuthChallengeDisposition, URLCredential?) -> Void
)
```

``` source
optional func urlSession(
    _ session: URLSession,
    task: URLSessionTask,
    didReceive challenge: URLAuthenticationChallenge
) async -> (URLSession.AuthChallengeDisposition, URLCredential?)
```

## Parameters 

`session`  

The session containing the task whose request requires authentication.

`task`  

The task whose request requires authentication.

`challenge`  

An object that contains the request for authentication.

`completionHandler`  

A handler that your delegate method must call. Its parameters are:

- `disposition`—One of several constants that describes how the challenge should be handled.

- `credential`—The credential that should be used for authentication if disposition is `NSURLSessionAuthChallengeUseCredential`; otherwise, `NULL`.

## Discussion

This method handles task-level authentication challenges. The URLSessionDelegate protocol also provides a session-level authentication delegate method. The method called depends on the type of authentication challenge:

- For session-level challenges—NSURLAuthenticationMethodNTLM, NSURLAuthenticationMethodNegotiate, NSURLAuthenticationMethodClientCertificate, or NSURLAuthenticationMethodServerTrust—the `NSURLSession` object calls the session delegate’s urlSession(_:didReceive:completionHandler:) method. If your app does not provide a session delegate method, the `NSURLSession` object calls the task delegate’s urlSession(_:task:didReceive:completionHandler:) method to handle the challenge.

- For non-session-level challenges (all others), the URLSession object calls the session delegate’s urlSession(_:task:didReceive:completionHandler:) method to handle the challenge. If your app provides a session delegate and you need to handle authentication, then you must either handle the authentication at the task level or provide a task-level handler that calls the per-session handler explicitly. The session delegate’s urlSession(_:didReceive:completionHandler:) method is *not* called for non-session-level challenges.

## See Also

### Handling authentication challenges

enum AuthChallengeDisposition

Constants passed by session or task delegates to the provided continuation block in response to an authentication challenge.

