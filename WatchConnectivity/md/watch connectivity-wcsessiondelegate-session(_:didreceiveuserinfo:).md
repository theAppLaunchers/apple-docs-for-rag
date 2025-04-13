

- Watch Connectivity
- WCSessionDelegate
-  session(\_:didReceiveUserInfo:) 

Instance Method

# session(\_:didReceiveUserInfo:)

Tells the delegate that the session successfully received a data directory from its counterpart.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.0+visionOS 1.0+watchOS 2.0+

``` source
optional func session(
    _ session: WCSession,
    didReceiveUserInfo userInfo: [String : Any] = [:]
)
```

## Parameters 

`session`  

The session object of the current process.

`userInfo`  

A dictionary of property list values representing the contents of the message. Use the contents of this dictionary to determine what course of action to take.

## Discussion

The session object calls this method when it successfully receives a data dictionary from its counterpart. Implement this method to incorporate the data into the app’s content.

The system calls this method on a background thread.

Warning

Always test Watch Connectivity data transfers on paired devices. The system doesn’t call the session(_:didReceiveUserInfo:) method in Simulator.

## See Also

### Managing Data Dictionary Transfers

func session(WCSession, didFinish: WCSessionUserInfoTransfer, error: (any Error)?)

Tells the delegate that a data transfer operation has finished successfully or ended because of an error.

