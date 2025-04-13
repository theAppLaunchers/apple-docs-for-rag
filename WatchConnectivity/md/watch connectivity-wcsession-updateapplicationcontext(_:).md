

- Watch Connectivity
- WCSession
-  updateApplicationContext(\_:) 

Instance Method

# updateApplicationContext(\_:)

Sends a dictionary of values that a paired and active device can use to synchronize its state.

iOS 9.0+iPadOS 9.0+Mac Catalyst 9.0+visionOS 1.0+watchOS 2.0+

``` source
func updateApplicationContext(_ applicationContext: [String : Any]) throws
```

## Parameters 

`applicationContext`  

A dictionary of property list values. You define the meaning of the dictionary contents. This parameter must not be `nil`.

## Discussion

Use this method to transfer a dictionary of data items to the counterpart app. The system sends context data when the opportunity arises, with the goal of having the data ready to use by the time the counterpart wakes up. The counterpart’s session delivers the data to the session(_:didReceiveApplicationContext:) method of its delegate. A counterpart can also retrieve the data from the receivedApplicationContext property of its session.

This method replaces the previous dictionary that was set, so you should use this method to communicate state changes or to deliver data that is updated frequently anyway. For example, this method is well suited for updating your app’s glance.

You may call this method when the counterpart is not currently reachable.

This method can only be called while the session is active—that is, the activationState property is set to WCSessionActivationState.activated. Calling this method for an inactive or deactivated session is a programmer error.

Handling Errors in Swift

In Swift, this method returns `Void` and is marked with the `throws` keyword to indicate that it throws an error in cases of failure.

You call this method in a `try` expression and handle any errors in the `catch` clauses of a `do` statement, as described in Error Handling in The Swift Programming Language and `About Imported Cocoa Error Parameters`.

## See Also

### Managing Background Updates

var applicationContext: [String : Any]

The most recent contextual data sent to the paired and active device.

var receivedApplicationContext: [String : Any]

A dictionary containing the last update data received from a paired and active device.

