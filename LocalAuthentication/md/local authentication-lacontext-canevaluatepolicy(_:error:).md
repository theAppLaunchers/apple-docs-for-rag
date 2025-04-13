

- Local Authentication
- LAContext
-  canEvaluatePolicy(\_:error:) 

Instance Method

# canEvaluatePolicy(\_:error:)

Assesses whether authentication can proceed for a given policy.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.10+visionOS 1.0+watchOS 3.0+

``` source
func canEvaluatePolicy(
    _ policy: LAPolicy,
    error: NSErrorPointer
) -> Bool
```

## Parameters 

`policy`  

The policy to evaluate. For possible values, see LAPolicy.

`error`  

If the method fails, it uses this parameter to return an error detailing what went wrong. See LAError.Code for possible error codes.

Specify `nil` for this parameter to ignore any errors.

## Return Value

true if the policy can be evaluated, otherwise false.

## Discussion

Some policies impose requirements that must be met before authentication can proceed. For example, a policy that requires biometrics can’t authenticate if Touch ID or Face ID is disabled. This method tests all the prerequisites for a given policy.

Don’t store the return value from this method because it might change as a result of changes in the system. For example, a user might disable Touch ID after you call this method.

Important

Don’t call this method in the reply block of the evaluatePolicy(_:localizedReason:reply:) method because that might lead to deadlock.

## See Also

### Checking availability

enum LAPolicy

The set of available local authentication policies.

var biometryType: LABiometryType

The type of biometric authentication supported by the device.

enum LABiometryType

The set of available biometric authentication types.

