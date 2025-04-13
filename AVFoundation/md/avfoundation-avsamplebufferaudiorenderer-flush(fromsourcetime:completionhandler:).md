

- AVFoundation
- AVSampleBufferAudioRenderer
-  flush(fromSourceTime:completionHandler:) 

Instance Method

# flush(fromSourceTime:completionHandler:)

Flushes queued sample buffers with presentation time stamps later than or equal to the specified time.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
func flush(
    fromSourceTime time: CMTime,
    completionHandler: @escaping (Bool) -> Void
)
```

``` source
func flush(fromSourceTime time: CMTime) async -> Bool
```

## Parameters 

`time`  

The time used to flush all later sample buffers.

`completionHandler`  

The block to invoke when the flush operation has either been completed or been interrupted. The block takes one argument:

flushSucceeded  
A Boolean value indicating whether the sample buffers were flushed.

## Discussion

This method can be used to replace media data scheduled to be rendered in the future, without interrupting playback. One example of this is when the data that has already been enqueued is from a sequence of two songs and the second song is swapped for a new song. In this case, this method would be called with the timestamp of the first sample buffer from the second song. After the completion handler is executed with a `YES` parameter, media data may again be enqueued with time stamps at the specified time.

 If `NO` is provided to the completion handler, the flush did not succeed and the set of enqueued sample buffers remains unchanged. A flush can fail because the source time was too close to (or earlier than) the current time or because the current configuration of the receiver does not support flushing at a particular time. In these cases, the caller can choose to flush all enqueued media data by invoking flush().

## See Also

### Removing Queued Buffers

let AVSampleBufferAudioRendererFlushTimeKey: String

The key that indicates the presentation timestamp of the first queued sample that was flushed.

