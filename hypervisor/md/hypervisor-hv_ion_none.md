

- Hypervisor
-  HV_ION_NONE 

Global Variable

# HV_ION_NONE

The value that represents a request for no notifications.

macOS

``` source
var HV_ION_NONE: Int { get }
```

## Discussion

Use this value to clear the I/O notifier’s notification request mask when you no longer want to receive notifications for any notifier event type. This only stops the delivery of notifications, it doesn’t remove notifiers. To remove a specific notifier use hv_vm_remove_pio_notifier(_:_:_:_:_:).

## See Also

### Notifier options

var HV_ION_ANY_SIZE: Int

The value that represents a request for notifications of an I/O result of any size.

var HV_ION_ANY_VALUE: Int

The value that represents a request for notifications of an I/O result that contains any value.

var HV_ION_EXIT_FULL: Int

The value that represents a request for notifications if the I/O queue is full.

