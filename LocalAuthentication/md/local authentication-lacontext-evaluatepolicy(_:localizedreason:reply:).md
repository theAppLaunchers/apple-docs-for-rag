

- Local Authentication
- LAContext
-  evaluatePolicy(\_:localizedReason:reply:) 

Instance Method

# evaluatePolicy(\_:localizedReason:reply:)

Evaluates the specified policy.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.10+visionOS 1.0+watchOS 3.0+

``` source
func evaluatePolicy(
    _ policy: LAPolicy,
    localizedReason: String,
    reply: @escaping (Bool, (any Error)?) -> Void
)
```

``` source
func evaluatePolicy(
    _ policy: LAPolicy,
    localizedReason: String
) async throws -> Bool
```

## Parameters 

`policy`  

The policy to evaluate. For possible values, see LAPolicy.

`localizedReason`  

The app-provided reason for requesting authentication, which displays in the authentication dialog presented to the user.

`reply`  

A closure that is executed when policy evaluation finishes. This is evaluated on a private queue internal to the framework in an unspecified threading context. You must not call canEvaluatePolicy(_:error:) in this block, because doing so could lead to deadlock.

success  
true if policy evaluation succeeded, otherwise false.

error  
`nil` if policy evaluation succeeded, an error object that should be presented to the user otherwise. See LAError.Code for possible error codes

## Discussion

Important

You can call this method from synchronous code using a completion handler, as shown on this page, or you can call it as an asynchronous method that has the following declaration:

```
func evaluatePolicy(_ policy: LAPolicy, localizedReason: String) async throws -> Bool
```

For information about concurrency and asynchronous code in Swift, see Calling Objective-C APIs Asynchronously.

This method asynchronously evaluates an authentication policy. Evaluating a policy may involve prompting the user for various kinds of interaction or authentication. The actual behavior is dependent on the evaluated policy and the device type. The behavior can also be affected by installed configuration profiles.

Note

To control the authentication prompt on devices that support it, attach the associated local authentication context to an LAAuthenticationView instance before calling this method.

In the localized string you present to the user in the authentication dialog, provide a clear reason for the authentication request, and describe the resulting action. Make the message short and clear, and provide it in the user’s language. Don’t include the app name, which already appears in the authentication dialog (in macOS, in the title of the dialog; in iOS, in the subtitle).

Don’t assume that a previous successful policy evaluation means that future evaluations will also succeed. Policy evaluation can fail for various reasons, including cancellation by the user or the system.

## See Also

### Evaluating authentication policies

var evaluatedPolicyDomainState: Data?

The current state of the evaluated policy domain.

Deprecated

var maxBiometryFailures: NSNumber?

The number of biometric authentication failures after which the context falls back to another mechanism.

Deprecated

