

- AVFoundation
- AVCaptureMetadataOutput
-  setMetadataObjectsDelegate(\_:queue:) 

Instance Method

# setMetadataObjectsDelegate(\_:queue:)

Sets the delegate and dispatch queue to use handle callbacks.

iOS 6.0+iPadOS 6.0+Mac Catalyst 14.0+macOS 13.0+tvOS 17.0+

``` source
func setMetadataObjectsDelegate(
    _ objectsDelegate: (any AVCaptureMetadataOutputObjectsDelegate)?,
    queue objectsCallbackQueue: dispatch_queue_t?
)
```

## Parameters 

`objectsDelegate`  

The delegate object to notify when new metadata objects become available. This object must conform to the AVCaptureMetadataOutputObjectsDelegate protocol.

`objectsCallbackQueue`  

The dispatch queue on which to execute the delegate’s methods. This queue must be a serial queue to ensure that metadata objects are delivered in the order in which they were received. If the `objectsDelegate` parameter is `nil`, you may specify `nil` for this parameter too; otherwise, you must specify a valid dispatch queue.

## Discussion

When new metadata objects are captured from the receiver’s connection, they are vended to the delegate object. All delegate methods are executed on the dispatch queue specified in the `objectsCallbackQueue` parameter. To ensure that metadata objects are processed in a timely manner and not dropped, you should specify a dispatch queue dedicated to processing the objects or that is otherwise not busy.

## See Also

### Receiving Captured Metadata Objects

var metadataObjectsDelegate: (any AVCaptureMetadataOutputObjectsDelegate)?

The delegate of the capture metadata output object.

var metadataObjectsCallbackQueue: dispatch_queue_t?

The dispatch queue on which to execute the delegate’s methods.

protocol AVCaptureMetadataOutputObjectsDelegate

Methods for receiving metadata produced by a metadata capture output.

