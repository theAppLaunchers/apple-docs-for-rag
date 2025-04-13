

- AppKit
- NSFilePromiseReceiver
-  receivePromisedFiles(atDestination:options:operationQueue:reader:) 

Instance Method

# receivePromisedFiles(atDestination:options:operationQueue:reader:)

Fulfills the promises at the specified destination.

macOS 10.12+

``` source
func receivePromisedFiles(
    atDestination destinationDir: URL,
    options: [AnyHashable : Any] = [:],
    operationQueue: OperationQueue,
    reader: @escaping (URL, (any Error)?) -> Void
)
```

## Parameters 

`destinationDir`  

The destination location URL of the file promise.

`options`  

An options dictionary to pass additional data.

`operationQueue`  

The operation queue on which to call the reader block when the promised file is ready.

`reader`  

A block to be called on the supplied operationQueue when the promised file is ready to be read.

## Discussion

Call this method only when you’re accepting the file promise. All file promise receivers in a drag must specify the same destination location. The `options` dictionary is ignored for now. The `reader` block is called on the supplied `operationQueue` when the promised file is ready to be read.

Avoid blocking the main thread while waiting for the file promise to be written (which can be a long process) by specifying an operation queue other than the main queue. When the source is an NSFilePromiseProvider, the reader block call is wrapped in a file coordination read.

Note

If writing the promised file fails, the `reader` block is still called with a non-nil `error`. There may be nothing in `fileURL`, or there may be a partial or corrupt file.

