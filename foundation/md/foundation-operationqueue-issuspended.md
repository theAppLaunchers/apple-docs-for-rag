

- Foundation
- OperationQueue
-  isSuspended 

Instance Property

# isSuspended

A Boolean value indicating whether the queue is actively scheduling operations for execution.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.1+macOS 10.5+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var isSuspended: Bool { get set }
```

## Discussion

When the value of this property is false, the queue actively starts operations that are in the queue and ready to execute. Setting this property to true prevents the queue from starting any queued operations, but already executing operations continue to execute. You may continue to add operations to a queue that is suspended but those operations are not scheduled for execution until you change this property to false.

Operations are removed from the queue only when they finish executing. However, in order to finish executing, an operation must first be started. Because a suspended queue does not start any new operations, it does not remove any operations (including cancelled operations) that are currently queued and not executing.

You may monitor changes to the value of this property using Key-value observing. Configure an observer to monitor the isSuspended key path of the operation queue.

The default value of this property is false.

