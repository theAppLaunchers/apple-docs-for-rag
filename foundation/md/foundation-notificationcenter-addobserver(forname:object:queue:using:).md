

- Foundation
- NotificationCenter
-  addObserver(forName:object:queue:using:) 

Instance Method

# addObserver(forName:object:queue:using:)

Adds an entry to the notification center to receive notifications that passed to the provided block.

iOS 4.0+iPadOS 4.0+Mac Catalyst 13.1+macOS 10.6+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func addObserver(
    forName name: NSNotification.Name?,
    object obj: Any?,
    queue: OperationQueue?,
    using block: @escaping (Notification) -> Void
) -> any NSObjectProtocol
```

## Parameters 

`name`  

The name of the notification to register for delivery to the observer block. Specify a notification name to deliver only entries with this notification name.

When `nil`, the sender doesn’t use notification names as criteria for delivery.

`obj`  

The object that sends notifications to the observer block. Specify a sender to deliver only notifications from this sender.

When `nil`, the notification center doesn’t use the sender as criteria for the delivery.

`queue`  

The operation queue where the `block` runs.

When `nil`, the block runs synchronously on the posting thread.

`block`  

The block that executes when receiving a notification.

The notification center copies the block. The notification center strongly holds the copied block until you remove the observer registration.

The block takes one argument: the notification.

## Return Value

An opaque object to act as the observer. Notification center strongly holds this return value until you remove the observer registration.

## Discussion

If a notification triggers more than one observer block, the blocks can all execute concurrently (but on their queue or on the current thread).

The following example shows how you can register to receive locale change notifications. It stores the return value from addObserver(forName:object:queue:using:) in an instance property called `localeChangeObserver`.

- Swift
- Objective-C

```
let center = NotificationCenter.default
let mainQueue = OperationQueue.main
localeChangeObserver = center.addObserver(
    forName: NSLocale.currentLocaleDidChangeNotification,
    object: nil,
    queue: mainQueue) { (note) in
        print("The user's locale changed to: \(NSLocale.current.identifier)")
    }
}
```

```
NSNotificationCenter *center = [NSNotificationCenter defaultCenter];
NSOperationQueue *mainQueue = [NSOperationQueue mainQueue];
self.localeChangeObserver = [center addObserverForName:NSCurrentLocaleDidChangeNotification object:nil
    queue:mainQueue usingBlock:^(NSNotification *note) {

        NSLog(@"The user's locale changed to: %@", [[NSLocale currentLocale] localeIdentifier]);
    }];
```

Unregister an observer to stop receiving notifications. To unregister an observer, use removeObserver(_:) or removeObserver(_:name:object:) with the most specific detail possible. For example, if you used a name and object to register the observer, use the name and object to remove it.

You must invoke removeObserver(_:) or removeObserver(_:name:object:) before the system deallocates any object that addObserver(forName:object:queue:using:) specifies.

- Swift
- Objective-C

```
let center = NotificationCenter.default
guard let localeChangeObserver = self.localeChangeObserver else { return }
center.removeObserver(localeChangeObserver)
```

```
NSNotificationCenter *center = [NSNotificationCenter defaultCenter];
[center removeObserver:self.localeChangeObserver];
```

Another common practice is to create a one-time notification by removing the observer from within the observation block, as in the following example.

- Swift
- Objective-C

```
let center = NotificationCenter.default
let mainQueue = OperationQueue.main
token = center.addObserver(
    forName: NSNotification.Name("OneTimeNotification"),
    object: nil,
    queue: mainQueue) {[weak self] (note) in
        print("Received the notification!")
        guard let token = self?.token else { return }
        center.removeObserver(token)
}
```

```
NSNotificationCenter * __weak center = [NSNotificationCenter defaultCenter];
self.token = [center addObserverForName:@"OneTimeNotification"
                                       object:nil
                                        queue:[NSOperationQueue mainQueue]
                                   usingBlock:^(NSNotification *note) {
                                       NSLog(@"Received the notification!");
                                       [center removeObserver:self.token];
                                   }];
```

This example stores the opaque observer object in an instance property called `token`, which you can use to remove the observer prior to receiving the notification.

Tip

To avoid a retain cycle, use a weak reference to `self` inside the block when `self` contains the observer as a strong reference.

## See Also

### Adding and Removing Notification Observers

func addObserver(Any, selector: Selector, name: NSNotification.Name?, object: Any?)

Adds an entry to the notification center to call the provided selector with the notification.

func removeObserver(Any, name: NSNotification.Name?, object: Any?)

Removes matching entries from the notification center’s dispatch table.

func removeObserver(Any)

Removes all entries specifying an observer from the notification center’s dispatch table.

