

- AVFoundation
- AVQueuedSampleBufferRendering
-  isReadyForMoreMediaData 

Instance Property

# isReadyForMoreMediaData

A Boolean value that indicates whether the receiver is able to accept more sample buffers.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+macOS 10.13+tvOS 11.0+visionOS 1.0+watchOS 4.0+

``` source
var isReadyForMoreMediaData: Bool { get }
```

**Required**

## Discussion

An object conforming to `AVQueuedSampleBufferRendering` keeps track of the occupancy levels of its internal queues for the benefit of clients that enqueue sample buffers from non-real-time sources, for example, clients that can supply sample buffers faster than they are consumed, and so need to decide when to hold back. Clients enqueueing sample buffers from non-real-time sources may hold off from generating or obtaining more sample buffers to enqueue when the value of `readyForMoreMediaData` is `NO`. It is safe to call enqueue(_:) when `readyForMoreMediaData` is `NO`, but don’t enqueue sample buffers without bound.

To help with control of the non-real-time supply of sample buffers, clients can call requestMediaDataWhenReady(on:using:) in order to specify a block that the receiver should invoke whenever it’s ready for sample buffers to be appended.

The value of `readyForMoreMediaData` often changes\` from `NO` to `YES` asynchronously, as previously supplied sample buffers are decoded and rendered.

This property is not key-value observable.

## See Also

### Requesting Media

func enqueue(CMSampleBuffer)

Sends a sample buffer to the queue for rendering.

**Required**

func requestMediaDataWhenReady(on: dispatch_queue_t, using: () -> Void)

Tells the target to invoke a client-supplied block in order to gather sample buffers for playback.

**Required**

func stopRequestingMediaData()

Cancels any current requestMediaDataWhenReady(on:using:) call.

**Required**

