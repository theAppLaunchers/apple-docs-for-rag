

- MapKit
- MKMapSnapshotter
-  start(with:completionHandler:) 

Instance Method

# start(with:completionHandler:)

Submits the request to create a snapshot and executes the resulting block on the specified queue.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+macOS 10.9+tvOS 9.2+visionOS 1.0+

``` source
func start(
    with queue: dispatch_queue_t,
    completionHandler: @escaping MKMapSnapshotter.CompletionHandler
)
```

``` source
func start(with queue: dispatch_queue_t) async throws -> MKMapSnapshotter.Snapshot
```

## Parameters 

`queue`  

The dispatch queue on which to execute the block that the `completionHandler` parameter specifies.

`completionHandler`  

The block to call with the resulting snapshot. This block can’t be `nil`.

## Discussion

Concurrency Note

You can call this method from synchronous code using a completion handler, as shown on this page, or you can call it as an asynchronous method that has the following declaration:

```
func start(with queue: dispatch_queue_t) async throws -> MKMapSnapshotter.Snapshot
```

For information about concurrency and asynchronous code in Swift, see Calling Objective-C APIs Asynchronously.

Call this method to begin generating a snapshot image based on the specified parameters. This method executes the request asynchronously. When rendering is complete, the snapshotter delivers the results to your block on the dispatch queue in the `queue` parameter.

The snapshotter delivers the final image to your app only when it’s running in the foreground. The snapshotter needs to render the final image while your app is in the foreground. If you start generating a snapshot while the app is in the background, or if your app moves to the background while a snapshot is in progress, this behavior delays the delivery of the snapshot until your app returns to the foreground.

In macOS, this method creates both standard and high-resolution representations of the map data and includes both in the returned image object. In iOS, you need to specify the image scale you want using the snapshot options, which defaults to the scale on the current device.

## See Also

### Generating a snapshot

func start(completionHandler: (MKMapSnapshotter.Snapshot?, (any Error)?) -> Void)

Submits the request to create a snapshot and delivers the results to the specified block.

typealias CompletionHandler

A block that processes the results of a snapshot request.

func cancel()

Cancels the request to create a snapshot.

var isLoading: Bool

A Boolean value that indicates whether the snapshotter is generating an image.

