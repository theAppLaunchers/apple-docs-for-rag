

- Dispatch
- DispatchIO
-  init(type:path:oflag:mode:queue:cleanupHandler:) 

Initializer

# init(type:path:oflag:mode:queue:cleanupHandler:)

Creates a new I/O channel that accesses the file at the specified path, potentially creating that file in the process.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOSSwift 4.0+

``` source
convenience init?(
    type: DispatchIO.StreamType,
    path: UnsafePointer,
    oflag: Int32,
    mode: mode_t,
    queue: DispatchQueue,
    cleanupHandler: @escaping (Int32) -> Void
)
```

## Parameters 

`type`  

The access semantics for the channel. For a list of possible values, see DispatchIO.StreamType.

`path`  

The absolute path of the file you want to open.

`oflag`  

The flags to pass to `open(2)` when opening the file at the specified path.

`mode`  

The mode flags to pass to `open(2)`. Specify `O_CREAT` to create the file at the specified path; otherwise, specify 0.

`queue`  

The dispatch queue on which to perform work.

`cleanupHandler`  

The handler to execute once the channel is closed. This block has no return value and takes the following parameter:

error  
An `errno` condition if creating or opening the channel failed; otherwise, the value is `0`.

## Discussion

This method opens the channel by passing the `path`, `oflag`, and mode parameters to the low-level `open(2)` function. The file descriptor returned by that function remains open and under system control until you close the channel, or until an error occurs that causes the channel to release the file descriptor. After closing the file descriptor, the channel executes the specified `cleanupHandler` block on `queue`.

## See Also

### Creating a Dispatch I/O Object

convenience init(type: DispatchIO.StreamType, fileDescriptor: Int32, queue: DispatchQueue, cleanupHandler: (Int32) -> Void)

Creates a new I/O channel that accesses the specified file descriptor.

convenience init(type: DispatchIO.StreamType, io: DispatchIO, queue: DispatchQueue, cleanupHandler: (Int32) -> Void)

Creates a new I/O channel from an existing I/O channel.

enum StreamType

The semantics for accessing the contents of a file descriptor.

