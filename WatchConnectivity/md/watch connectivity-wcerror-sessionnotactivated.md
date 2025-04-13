

- Watch Connectivity
- WCError
-  sessionNotActivated 

Type Property

# sessionNotActivated

An error indicating that the other device doesn’t have an active session.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+visionOS 1.0+watchOS 2.0+

``` source
static var sessionNotActivated: WCError.Code { get }
```

## See Also

### Understanding Error Codes

static var genericError: WCError.Code

An error that occurs when there is an unknown problem.

static var sessionNotSupported: WCError.Code

An error indicating that the current device doesn’t support the use of session objects.

static var sessionMissingDelegate: WCError.Code

An error indicating that the WatchKit extension doesn’t have a valid extension delegate to process events.

static var deviceNotPaired: WCError.Code

An error indicating that the current device doesn’t have a paired counterpart.

static var watchAppNotInstalled: WCError.Code

An error indicating that the Watch app isn’t an installed app on the user’s Apple Watch.

static var notReachable: WCError.Code

An error indicating that the counterpart app isn’t reachable.

static var invalidParameter: WCError.Code

An error indicating that a parameter is invalid.

static var payloadTooLarge: WCError.Code

An error indicating an attempt to send an item that exceeds the maximum size limit.

static var payloadUnsupportedTypes: WCError.Code

An error indicating that a dictionary contains nonproperty list types.

static var messageReplyFailed: WCError.Code

An error that occurs when the system can’t return the reply.

static var messageReplyTimedOut: WCError.Code

An error that occurs when the counterpart app doesn’t return a reply in time.

static var fileAccessDenied: WCError.Code

An error indicating that the system can’t transfer a file because it is inaccessible.

static var deliveryFailed: WCError.Code

An error that occurs when the system can’t deliver the payload.

static var insufficientSpace: WCError.Code

An error indicating that there isn’t enough space on the receiving side to store the data.

static var sessionInactive: WCError.Code

An error indicating that the session is inactive.

