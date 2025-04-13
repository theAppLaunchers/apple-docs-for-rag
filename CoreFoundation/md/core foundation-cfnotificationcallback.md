

- Core Foundation
-  CFNotificationCallback 

Type Alias

# CFNotificationCallback

Callback function invoked for each observer of a notification when the notification is posted.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
typealias CFNotificationCallback = (CFNotificationCenter?, UnsafeMutableRawPointer?, CFNotificationName?, UnsafeRawPointer?, CFDictionary?) -> Void
```

## Parameters 

`center`  

The notification center handling the notification.

`observer`  

An arbitrary value, other than `NULL`, that identifies the observer.

`name`  

The name of the notification being posted.

`object`  

An arbitrary value that identifies the object posting the notification. For distributed notifications, `object` is always a CFString object. This value could be `NULL`.

`userInfo`  

A dictionary containing additional information regarding the notification. This value could be `NULL`.

If the notification center is a Darwin notification center, this value must be ignored.

