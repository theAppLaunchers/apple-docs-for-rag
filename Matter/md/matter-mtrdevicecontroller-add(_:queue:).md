

- Matter
- MTRDeviceController
-  add(\_:queue:) 

Instance Method

# add(\_:queue:)

Adds a Delegate to the device controller as well as the Queue on which the Delegate callbacks will be triggered

iOS 18.2+iPadOS 18.2+Mac Catalyst 18.2+macOS 15.2+tvOS 18.2+visionOS 2.2+watchOS 11.2+

``` source
func add(
    _ delegate: any MTRDeviceControllerDelegate,
    queue: dispatch_queue_t
)
```

## Discussion

Multiple delegates can be added to monitor MTRDeviceController state changes. Note that there should only be one delegate that responds to pairing related callbacks.

If a delegate is added a second time, the call would be ignored.

All delegates are held by weak references, and so if a delegate object goes away, it will be automatically removed.

