

- Watch Connectivity
- WCSession
-  activate() 

Instance Method

# activate()

Activates the session asynchronously.

iOS 9.0+iPadOS 9.0+Mac Catalyst 9.0+visionOS 1.0+watchOS 2.0+

``` source
func activate()
```

## Discussion

This method executes asynchronously and calls the session(_:activationDidCompleteWith:error:) method of your delegate object upon completion. Call this method when your app is ready to communicate with its counterpart. Your cannot send or receive messages until you call this method. If the delegate property is `nil`, calling this method logs an error.

In watchOS 2.1 and earlier, this method activates the session synchronously and always results in an active session.

## See Also

### Configuring the Session

var delegate: (any WCSessionDelegate)?

The delegate for the session object

var activationState: WCSessionActivationState

The current activation state of the session.

