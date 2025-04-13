

- Watch Connectivity
- WCSessionDelegate
-  sessionDidBecomeInactive(\_:) 

Instance Method

# sessionDidBecomeInactive(\_:)

Tells the delegate that the session will stop communicating with the current Apple Watch.

iOS 9.3+iPadOS 9.3+Mac Catalyst 13.1+visionOS 1.0+

``` source
func sessionDidBecomeInactive(_ session: WCSession)
```

**Required**

## Parameters 

`session`  

The session object whose activation state changed.

## Discussion

You must implement this method to support quick switching between Apple Watch devices in your iPhone app. The session calls this method when it detects that the user has switched to a different Apple Watch. While in the inactive state, the session delivers any pending data to your delegate object and prevents you from initiating any new data transfers. After the last transfer finishes, the session moves to the deactivated state.

Use this method to update any private data structures that might be affected by the impending change to the active Apple Watch. For example, you might clean up data structures and close files related to outgoing content.

## See Also

### Managing Session Activation

func session(WCSession, activationDidCompleteWith: WCSessionActivationState, error: (any Error)?)

Tells the delegate that the session has finished activating.

**Required**

func sessionDidDeactivate(WCSession)

Tells the delegate that the session has delivered all the data from the previous session, and that communication with the Apple Watch has ended.

**Required**

