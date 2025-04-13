

- AVFoundation
- AVPlayerItemMetadataOutput
-  advanceIntervalForDelegateInvocation 

Instance Property

# advanceIntervalForDelegateInvocation

The time interval, in seconds, the player item metadata output object messages its delegate earlier than normal.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 1.0+

``` source
var advanceIntervalForDelegateInvocation: TimeInterval { get set }
```

## Discussion

If possible, an `AVPlayerItemMetadataOutput` will message its delegate `advanceIntervalForDelegateInvocation` seconds earlier than otherwise. If the value you provide is large, effectively requesting provision of samples earlier than the `AVPlayerItemMetadataOutput` is prepared to act on them, the delegate will be invoked as soon as possible.

## See Also

### Configuring the Delegate

var delegate: (any AVPlayerItemMetadataOutputPushDelegate)?

The delegate object.

protocol AVPlayerItemMetadataOutputPushDelegate

Methods you can implement to provide additional metadata.

var delegateQueue: dispatch_queue_t?

The dispatch queue on which messages are sent to the delegate.

func setDelegate((any AVPlayerItemMetadataOutputPushDelegate)?, queue: dispatch_queue_t?)

Sets the delegate and a dispatch queue on which the delegate is called.

