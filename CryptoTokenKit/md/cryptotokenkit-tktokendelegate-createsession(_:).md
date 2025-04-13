

- CryptoTokenKit
- TKTokenDelegate
-  createSession(\_:) 

Instance Method

# createSession(\_:)

Tells the delegate to create a session for the specified token.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+macOS 10.12+tvOS 11.0+visionOS 1.0+watchOS 4.0+

``` source
func createSession(_ token: TKToken) throws -> TKTokenSession
```

**Required**

## Parameters 

`token`  

The token.

## Return Value

A new token session, or `nil` if an error occurred.

## Discussion

All operations for a token are performed within a session representing an authentication context. This delegate method is called whenever new authentication context is needed. For example, a client may want to perform a token operation using a keychain object that has an associated `LAContext`.

## See Also

### Delegate Methods

func token(TKToken, terminateSession: TKTokenSession)

Tells the delegate to terminate the specified token session.

