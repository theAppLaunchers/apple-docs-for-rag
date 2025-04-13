

- USBDriverKit
- IOUSBHostPipe
-  AsyncIOBundled 

Instance Method

# AsyncIOBundled

Enqueues a contiguous group of requests from the descriptor ring.

DriverKit 19.0+

``` source
kern_return_t AsyncIOBundled(uint32_t ioTransferIndex, uint32_t ioTransferCount, uint32_t * ioTransferAcceptedCount, const uint32_t dataBufferLengthArray[16], int dataBufferLengthArrayCount, OSAction * completion, uint32_t completionTimeoutMs);
```

## Parameters 

`ioTransferIndex`  

The index of the first ring element to transfer.

`ioTransferCount`  

The number of ring elements to transfer.

`ioTransferAcceptedCount`  

A pointer to a variable. On return, this variable contains the number of ring elements that the method enqueued successfully.

`dataBufferLengthArray`  

An array of integers, each of which contains the amount of data to transfer for an element. The first integer in the array contains the length of the buffer for the element at the index `ioTransferIndex`. The next integer contains the length of the buffer for the next element in the ring, and so on.

`dataBufferLengthArrayCount`  

The number of elements in the `dataBufferLengthArray` parameter. The value in this parameter must match the value in `ioTransferCount`.

`completion`  

The action object containing a completion function to call when the transfers finish. Your callback method must conform to the CompleteAsyncIOBundled method. This parameter must not be `NULL`.

`completionTimeoutMs`  

The timeout value in milliseconds. Specify `0` if you don’t want the request to time out. You must specify `0` when transferring data on an interrupt endpoint.

## Return Value

kIOReturnSuccess on success, or another value if an error occurs. See Error Codes.

## Discussion

This method performs a bulk transfer of multiple data buffers. Use this method on bulk pipes to reduce the messaging overhead when you need to transfer large amounts of data to or from the device. Don’t use this method with interrupt or isochonous pipes.

This method requires you to use a memory descriptor ring to store the data buffers involved in the transfer. Create a ring for the current pipe using CreateMemoryDescriptorRing and populate the buffers for each ring element using the SetMemoryDescriptor method. When sending data to the device, fill several of the ring’s data buffers with content before calling this method. When receiving data, calling this method asks the system to fill the data buffers of the specified ring elements.

When you enqueue a set of buffers, this method automatically handles wraparound conditions in the ring. For example, if the index of the next element to enqueue is beyond the end of the ring, the method automatically wraps around to the beginning of the ring. However, you are still responsible for keeping track of which data buffers your code has read or written.

When all transfers are complete, the system executes the callback you provided in the `completion` parameter. In your completion handler, verify that the number of transferred elements matches the number that you requested.

## See Also

### Interacting with Descriptor Rings

kern_return_t CreateMemoryDescriptorRing(uint32_t size);

kern_return_t SetMemoryDescriptor(IOMemoryDescriptor * memoryDescriptor, uint32_t index);

CompleteAsyncIOBundled

Handles the completion of an asynchronous bundled transfer.

Bundling Constants

Constants associated with bulk I/O transfers.

