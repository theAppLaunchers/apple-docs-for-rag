

- AVFoundation
- AVPlayer
-  addPeriodicTimeObserver(forInterval:queue:using:) 

Instance Method

# addPeriodicTimeObserver(forInterval:queue:using:)

Requests the periodic invocation of a given block during playback to report changing time.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
nonisolated
func addPeriodicTimeObserver(
    forInterval interval: CMTime,
    queue: dispatch_queue_t?,
    using block: @escaping (CMTime) -> Void
) -> Any
```

## Parameters 

`interval`  

The time interval at which the system invokes the block during normal playback, according to progress of the player’s current time.

`queue`  

The dispatch queue on which the system calls the block. Passing a concurrent queue isn’t supported and results in undefined behavior.

If you pass `NULL`, the system uses the main queue.

`block`  

The block that the system periodically invokes.

The block takes a single parameter:

time  
The time at which the system invokes the block.

## Return Value

An opaque object that you pass as the argument to removeTimeObserver(_:) to cancel observation.

## Mentioned in 

Monitoring playback progress in your app

## Discussion

You must maintain a strong reference to the returned value as long as you want the time observer to be invoked by the player. You must pair each invocation of this method with a corresponding call to removeTimeObserver(_:). Releasing the observer object without invoking removeTimeObserver(_:) results in undefined behavior.

The system invokes the block periodically at the interval specified, interpreted according to the timeline of the current item. It also invokes the block whenever time jumps or playback starts or stops. If the interval corresponds to a very short interval in real time, the player may invoke the block less frequently than your app requested. Even so, the player will invoke the block sufficiently often for the client to update indications of the current time appropriately in its end-user interface.

The following example illustrates how you set up a callback the system invokes every half second during normal playback.

- Swift
- Objective-C

```
func addPeriodicTimeObserver() {
    // Invoke callback every half second
    let interval = CMTime(seconds: 0.5,
                          preferredTimescale: CMTimeScale(NSEC_PER_SEC))
    // Add time observer. Invoke closure on the main queue.
    timeObserverToken =
        player.addPeriodicTimeObserver(forInterval: interval, queue: .main) {
            [weak self] time in
            // update player transport UI
    }
}
```

```
- (void)addPeriodicTimeObserver {
    // Invoke callback every half second
    CMTime interval = CMTimeMakeWithSeconds(0.5, NSEC_PER_SEC);
    // Queue on which to invoke the callback
    dispatch_queue_t mainQueue = dispatch_get_main_queue();
    // Add time observer
    self.timeObserverToken =
        [self.player addPeriodicTimeObserverForInterval:interval
                                                  queue:mainQueue
                                             usingBlock:^(CMTime time) {
            // Use weak reference to self
            // Update player transport UI
        }];
}
```

Important

Use a `weak` reference to `self` in the callback block to prevent creating a retain cycle.

## See Also

### Observing Playback Time

func currentTime() -> CMTime

Returns the current time of the current player item.

func addBoundaryTimeObserver(forTimes: [NSValue], queue: dispatch_queue_t?, using: () -> Void) -> Any

Requests the invocation of a block when specified times are traversed during normal playback.

func removeTimeObserver(Any)

Cancels a previously registered periodic or boundary time observer.

