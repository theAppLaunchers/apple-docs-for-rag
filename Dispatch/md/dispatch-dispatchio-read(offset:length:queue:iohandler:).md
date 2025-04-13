

- Dispatch
- DispatchIO
-  read(offset:length:queue:ioHandler:) 

Instance Method

# read(offset:length:queue:ioHandler:)

Schedules an asynchronous read operation on the specified channel.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
func read(
    offset: off_t,
    length: Int,
    queue: DispatchQueue,
    ioHandler: @escaping (Bool, DispatchData?, Int32) -> Void
)
```

## Parameters 

`offset`  

For random-access channels, this parameter specifies the offset into the channel from which to read. The offset is specified relative to the initial file pointer of the channel’s file descriptor at the time the channel was created. For stream-based channels, this parameter is ignored and data is read from the current position.

`length`  

The number of bytes to read from the channel. Specify `SIZE_MAX` to continue reading data until an EOF is reached.

`queue`  

The dispatch queue on which to submit the `ioHandler` closure.

`ioHandler`  

The closure to use to process the data read from the channel. This block may be queued multiple times to process a given data request. Each time the block is queued, the `data` parameter passed to the handler contains the most recently read chunk of data. The handler has no return value and takes the following parameters:

done  
A Boolean value indicating whether the operation is complete.

data  
A DispatchData object containing the data read from the file descriptor.

error  
An `errno` condition if there was an error; otherwise, the value is `0`.

Your block need not be reentrant. The system guarantees that only one instance of this block will be executed at any given time.

## Discussion

This function reads the specified data and submits the handler block to queue to process the data. If the `done` parameter of the handler is set to false, it means that only part of the data was read. If the `done` parameter is true, it means the read operation is complete and the handler will not be submitted again. If an unrecoverable error occurs on the channel’s file descriptor, the `done` parameter is set to true and an appropriate error value is reported in the handler’s error parameter.

If the handler is submitted with the done parameter set to true, an empty data object, and an error code of 0, it means that the channel reached the end of the file.

## See Also

### Reading from the File

class func read(fromFileDescriptor: Int32, maxLength: Int, runningHandlerOn: DispatchQueue, handler: (DispatchData, Int32) -> Void)

Schedules an asynchronous read operation using the specified file descriptor.

