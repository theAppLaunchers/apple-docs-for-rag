

- Core Foundation
-  CFNotificationCenterGetDarwinNotifyCenter() 

Function

# CFNotificationCenterGetDarwinNotifyCenter()

Returns the application’s Darwin notification center.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
func CFNotificationCenterGetDarwinNotifyCenter() -> CFNotificationCenter!
```

## Return Value

The application’s Darwin notification center.

## Discussion

This notification center is used to cover the `` Core OS notification mechanism (see `/usr/include/notify.h`). An application has only one Darwin notification center, so this function returns the same value each time it is called.

The Darwin Notify Center has no notion of per-user sessions, all notifications are system-wide. As with distributed notifications, the main thread’s run loop must be running in one of the common modes (usually `kCFRunLoopDefaultMode`) for Darwin-style notifications to be delivered.

Important

Several function parameters are ignored by Darwin notification centers. To ensure future compatibility, you should pass `NULL` or `0` for all ignored arguments.

## See Also

### Accessing a Notification Center

func CFNotificationCenterGetDistributedCenter() -> CFNotificationCenter!

Returns the application’s distributed notification center.

func CFNotificationCenterGetLocalCenter() -> CFNotificationCenter!

Returns the application’s local notification center.

