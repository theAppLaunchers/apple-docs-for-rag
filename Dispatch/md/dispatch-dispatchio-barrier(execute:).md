

- Dispatch
- DispatchIO
-  barrier(execute:) 

Instance Method

# barrier(execute:)

Schedules a barrier operation on the specified channel.

iOS 5.0+iPadOS 5.0+Mac Catalyst 13.1+macOS 10.7+tvOSvisionOS 1.0+watchOS 2.0+

``` source
func barrier(execute barrier: @escaping () -> Void)
```

## Parameters 

`barrier`  

The block to execute when all previously scheduled operations on the channel have completed.

## Discussion

A barrier operation is a way to ensure that no new channel-related operations is executed until all previous operations have completed and the specified `barrier` block has been executed. The barrier operation applies to the channel’s file descriptor and not to a specific channel. In other words, if multiple channels are associated with the same file descriptor, a barrier operation scheduled on any of the channels acts as a barrier across all of the channels. All previously scheduled operations on any of those channels must complete before the barrier block is executed.

While the barrier block is running, it may safely operate on the channel’s underlying file descriptor using `fsync`, `lseek`, and similar functions, but the block must not close the file descriptor.

