

- WatchKit
- WKUserNotificationInterfaceController
-  didReceive(\_:withCompletion:) Deprecated

Instance Method

# didReceive(\_:withCompletion:)

Delivers a notification object to your interface controller for processing.

watchOS 3.0–5.0Deprecated

``` source
@MainActor
func didReceive(
    _ notification: UNNotification,
    withCompletion completionHandler: @escaping (WKUserNotificationInterfaceType) -> Void
)
```

Deprecated

Use didReceive(_:) instead.

## Parameters 

`notification`  

The notification object that triggered this event.

`completionHandler`  

The completion handler for telling the system what interface to display. Execute this completion handler at the end of your method implementation. If you do not execute this block in a timely manner, the system displays your app’s static notification interface. This block has no return value and takes the following parameter:

interface  
The notification interface to be displayed. Specify the value WKUserNotificationInterfaceType.custom to display your dynamic interface. Specify the value WKUserNotificationInterfaceType.default to display the static interface. You might choose to display the static interface if the payload does not contain the data you were expecting.

## Discussion

Before displaying your notification interface, WatchKit calls this method to deliver the payload of the incoming remote notification. Implement this method and use it to store the notification dictionary, configure your custom notification interface, and execute the `completionHandler` block as quickly as possible. Failure to execute the completion handler in a timely manner will cause the system to display the corresponding static notification interface.

WatchKit may call this method multiple times while your interface controller is active. If a new remote notification with the same category arrives while your notification interface is active, WatchKit calls the method again with the new remote notification payload.

## See Also

### Processing the Notification

func didReceive(UNNotification)

Delivers a notification object to your interface controller for processing.

