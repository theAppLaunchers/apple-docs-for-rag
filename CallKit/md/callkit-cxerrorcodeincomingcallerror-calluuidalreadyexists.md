

- CallKit
- CXErrorCodeIncomingCallError
-  callUUIDAlreadyExists 

Type Property

# callUUIDAlreadyExists

The incoming call UUID already exists.

iOS 10.0+iPadOS 10.0+Mac Catalyst 10.0+visionOS 1.0+watchOS 9.0+

``` source
static var callUUIDAlreadyExists: CXErrorCodeIncomingCallError.Code { get }
```

## See Also

### Errors

static var filteredByBlockList: CXErrorCodeIncomingCallError.Code

The system is filtering the incoming call because the user is blocking it.

static var filteredByDoNotDisturb: CXErrorCodeIncomingCallError.Code

The system is filtering the incoming call because Do Not Disturb is active and the incoming caller isn’t a VIP.

static var unentitled: CXErrorCodeIncomingCallError.Code

The app doesn’t have the entitlement to receive incoming calls.

static var unknown: CXErrorCodeIncomingCallError.Code

An unknown error occurred.

