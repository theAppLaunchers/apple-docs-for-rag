

- Metal
- Resource Synchronization
-  Synchronizing Events Between a GPU and the CPU 

Article

# Synchronizing Events Between a GPU and the CPU

Use shareable events to synchronize your app’s work between a GPU and the CPU.

## Overview

A shared event has methods and properties that let your app execute code when the event is triggered, or update the event’s value.

Call the notify(_:atValue:block:) method to register a notification handler that listens for changes to a shared event’s value. When some other action signals the event to give it a new value that is equal or larger than this value, such as when you signal the event from a command you sent to the GPU, the notification handler executes the block of code that you provided.

Set the shared event’s signaledValue property to signal the event from the CPU. The value is only updated if you set a value larger than the current value stored in the event. Setting the value unblocks any commands waiting on a value equal to or smaller than the new value, and similarly triggers any CPU-based notifications.

The following figure and code show a shareable event that synchronizes GPU work and CPU work.

- Swift
- Objective-C

```
func setupGPUCPUEvent() {
    // Shareable event
    sharedEvent = device.makeSharedEvent()

    // Shareable event listener
    let myQueue = DispatchQueue(label: "com.example.apple-samplecode.MyQueue")
    sharedEventListener = MTLSharedEventListener(dispatchQueue: myQueue)
}

func synchronizeGPUCPUEvent() {
    guard
        let sharedEvent = sharedEvent,
        let sharedEventListener = sharedEventListener,
        let commandBuffer = commandQueue.makeCommandBuffer()
        else { return }

    // Register CPU work
    sharedEvent.notify(sharedEventListener, atValue: 2) { (sEvent, value) in
        /* Do CPU work */
        sEvent.signaledValue = 3
    }

    // Encode GPU work
    /* Encode GPU work part 1 */
    commandBuffer.encodeSignalEvent(sharedEvent, value: 1)
    /* Encode GPU work part 2 */
    commandBuffer.encodeSignalEvent(sharedEvent, value: 2)
    commandBuffer.encodeWaitForEvent(sharedEvent, value: 3)
    /* Encode GPU work part 3 */
    commandBuffer.commit()
}
```

```
- (void)setupGPUCPUEvent
{
    // Shareable event
    _sharedEvent = [_device newSharedEvent];

    // Shareable event listener
    dispatch_queue_t myQueue = dispatch_queue_create("com.example.apple-samplecode.MyQueue", NULL);
    _sharedEventListener = [[MTLSharedEventListener alloc] initWithDispatchQueue:myQueue];
}

- (void)renderFrame
{
    // Register CPU work
    [_sharedEvent notifyListener:_sharedEventListener
                         atValue:2
                           block:^(id sharedEvent, uint64_t value) {
        /* Do CPU work */
        sharedEvent.signaledValue = 3;
    }];

    // Encode GPU work
    id commandBuffer = [_commandQueue commandBuffer];
    /* Encode GPU work part 1 */
    [commandBuffer encodeSignalEvent:_sharedEvent value:1];
    /* Encode GPU work part 2 */
    [commandBuffer encodeSignalEvent:_sharedEvent value:2];
    [commandBuffer encodeWaitForEvent:_sharedEvent value:3];
    /* Encode GPU work part 3 */
    [commandBuffer commit];
}
```

The setup code creates a shareable event and a listener object. Listener objects are used to dispatch notifications to the app when the event is signaled.

The work for this task is shared between the GPU and the CPU. As you can see in the figure above, the code needs to execute in the following order:

1.  GPU work part 1

2.  GPU work part 2

3.  CPU work

4.  GPU part 3

The `setupGPUCPUEvent` function uses signals to enforce this execution order. First, the function registers an event handler to be executed when the event is signaled. When called, this event handler executes the code for step 3 and then signals the event. That completes the CPU portion of the task.

Next, the function encodes the work for the GPU. It encodes the work for part 1, signals the event, and then does the same for part 2, and signals the event again. Part 3 of the GPU code needs to run after the event handler finishes executing, so next the function encodes a command to wait for the CPU to signal the event. After this, the function encodes the commands for part 3 and commits the command buffer for execution.

When the function commits the command buffer, the following actions occur:

1.  The GPU executes the first part of the task.

2.  The GPU signals the event to a new value of 1.

3.  The GPU executes the second part of the task.

4.  The GPU signals the event to a new value of 2.

5.  The CPU detects the signal value and runs the notification handler.

6.  The notification handler signals the event to a new value of 3.

7.  The GPU detects the signal value and executes the remaining commands.

## See Also

### Signal Events

Implementing a Multistage Image Filter Using Heaps and Events

Use events to synchronize access to resources allocated on a heap.

About Synchronization Events

Synchronize access to resources in your app by signaling events.

Synchronizing Events Within a Single Device

Use nonshareable events to synchronize your app’s work within a single device.

Synchronizing Events Across Multiple Devices or Processes

Use shareable events to synchronize your app’s work across multiple devices or processes.

protocol MTLEvent

A simple semaphore to synchronize access to Metal resources.

protocol MTLSharedEvent

An object you use to synchronize access to Metal resources across multiple CPUs, GPUs, and processes.

class MTLSharedEventHandle

An object you use to recreate a shareable event.

class MTLSharedEventListener

A listener for shareable event notifications.

typealias MTLSharedEventNotificationBlock

A block of code invoked after a shareable event’s signal value equals or exceeds a given value.

