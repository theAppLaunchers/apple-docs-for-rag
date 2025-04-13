

- Dispatch
-  DISPATCH_IO_RANDOM 

Global Variable

# DISPATCH_IO_RANDOM

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
var DISPATCH_IO_RANDOM: Int32 { get }
```

## Discussion

The channel represents a random access file. Read and write operations may be performed concurrently with a channel of this type. Offsets are interpreted relative to the file pointer position that is current at the time the channel is created. After channel creation, the file pointer position of the file descriptor is indeterminate until channel relinquishes control of the file descriptor, at which time the position is reset to its initial value.

The file descriptor for a channel of this type must be seekable. If it is not, attempting to create a channel of this type for the descriptor will result in an error.

## See Also

### Initializing the Type

var DISPATCH_IO_STREAM: Int32

