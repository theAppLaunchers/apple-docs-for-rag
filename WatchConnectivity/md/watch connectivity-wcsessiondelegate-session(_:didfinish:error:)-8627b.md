

- Watch Connectivity
- WCSessionDelegate
-  session(\_:didFinish:error:) 

Instance Method

# session(\_:didFinish:error:)

Tells the delegate that a data transfer operation has finished successfully or ended because of an error.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+visionOS 1.0+watchOS 2.0+

``` source
optional func session(
    _ session: WCSession,
    didFinish userInfoTransfer: WCSessionUserInfoTransfer,
    error: (any Error)?
)
```

## Parameters 

`session`  

The session object of the current process.

`userInfoTransfer`  

An object containing information about the data that was transferred.

`error`  

An error object if a problem occurred.

## Discussion

The session object calls this method when a data transfer initiated by the current app finished, either successfully or unsuccessfully. Use this method to note that the transfer completed or to respond to errors, perhaps by trying to send the data again at a later time.

This method is called on a background thread of your app.

## See Also

### Managing Data Dictionary Transfers

func session(WCSession, didReceiveUserInfo: [String : Any])

Tells the delegate that the session successfully received a data directory from its counterpart.

