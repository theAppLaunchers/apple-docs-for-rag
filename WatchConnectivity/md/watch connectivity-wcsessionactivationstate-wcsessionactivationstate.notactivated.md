

- Watch Connectivity
- WCSessionActivationState
-  WCSessionActivationState.notActivated 

Case

# WCSessionActivationState.notActivated

The session is not activated. When in this state, no communication occurs between the Watch app and iOS app. It is a programmer error to try to send data to the counterpart app while in this state.

iOS 9.3+iPadOS 9.3+Mac Catalyst 13.1+visionOS 1.0+watchOS 2.2+

``` source
case notActivated
```

## See Also

### Constants

case inactive

The session was active but is transitioning to the deactivated state. The session’s delegate object may still receive data while in this state, but it is a programmer error to try to send data to the counterpart app.

case activated

The session is active and the Watch app and iOS app may communicate with each other freely.

