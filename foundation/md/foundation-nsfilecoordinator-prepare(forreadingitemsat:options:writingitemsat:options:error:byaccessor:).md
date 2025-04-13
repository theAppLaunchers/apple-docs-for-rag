

- Foundation
- NSFileCoordinator
-  prepare(forReadingItemsAt:options:writingItemsAt:options:error:byAccessor:) 

Instance Method

# prepare(forReadingItemsAt:options:writingItemsAt:options:error:byAccessor:)

Prepare to read or write from multiple files in a single batch operation.

iOS 5.0+iPadOS 5.0+Mac Catalyst 13.1+macOS 10.7+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func prepare(
    forReadingItemsAt readingURLs: [URL],
    options readingOptions: NSFileCoordinator.ReadingOptions = [],
    writingItemsAt writingURLs: [URL],
    options writingOptions: NSFileCoordinator.WritingOptions = [],
    error outError: NSErrorPointer,
    byAccessor batchAccessor: (@escaping () -> Void) -> Void
)
```

## Parameters 

`readingURLs`  

An array of NSURL objects identifying the items you want to read.

`readingOptions`  

One of the reading options described in NSFileCoordinator.ReadingOptions. If you pass `0` for this parameter, the savePresentedItemChanges(completionHandler:) method of relevant file presenters is called before your block executes.

`writingURLs`  

An array of NSURL objects identifying the items you want to write.

`writingOptions`  

One of the writing options described in NSFileCoordinator.WritingOptions. The options you specify partially determine how file presenters are notified and how this file coordinator object waits to execute your block.

`outError`  

On input, a pointer to a pointer for an error object. If a file presenter encounters an error while preparing for this operation, that error is returned in this parameter and the block in the `writer` parameter is not executed. If you cancel this operation before the `batchAccessor` block is executed, this parameter contains an error object on output.

`batchAccessor`  

A Block object containing additional calls to methods of this class.

The block takes the following parameter:

completionHandler  
A completion handler block. The batch accessor must call the completion handler when it has finished its read and write calls.

## Discussion

Use this method to prepare the file coordinator for multiple read and write operations. Because file coordination requires interprocess communication, it is much more efficient to batch changes to large numbers of files and directories than to change each item individually. The file coordinator uses the values in the `readingURLs` and `writingURLs` parameters, together with reading and writing options, to prepare any relevant file presenters for the upcoming operations. Specifically, it uses these parameters in the same way as the coordinate(readingItemAt:options:error:byAccessor:) and coordinate(writingItemAt:options:error:byAccessor:) methods to determine which file presenter methods to call.

This method executes synchronously, blocking the current thread until the `batchAccessor` block finishes executing. The block you provide for the `batchAccessor` parameter does not perform the actual operations itself. Instead, you must call the individual coordinated read and write methods from inside the `batchAccessor` block. You must then call the completion handler after all the coordinated reads and writes have completed. You can call the completion handler from any thread.

Don’t simply pass this method all the URLs that are passed into the nested coordinate methods. Instead pass only the top-level files and directories involved in the operation. This method triggers messages to the file presenters of those items and to the file presenters of any items contained by those items.

In most cases, passing the same reading and writing options to both this method and the contained coordination operations is redundant. For example, it is often appropriate to pass withoutChanges to nested read operations. This method has already triggered a call to savePresentedItemChanges(completionHandler:). The individual read operations do not need to trigger additional calls.

## See Also

### Related Documentation

func coordinate(with: [NSFileAccessIntent], queue: OperationQueue, byAccessor: ((any Error)?) -> Void)

Performs a number of coordinated-read or -write operations asynchronously.

### Coordinating File Operations Synchronously

func coordinate(readingItemAt: URL, options: NSFileCoordinator.ReadingOptions, error: NSErrorPointer, byAccessor: (URL) -> Void)

Initiates a read operation on a single file or directory using the specified options.

func coordinate(writingItemAt: URL, options: NSFileCoordinator.WritingOptions, error: NSErrorPointer, byAccessor: (URL) -> Void)

Initiates a write operation on a single file or directory using the specified options.

func coordinate(readingItemAt: URL, options: NSFileCoordinator.ReadingOptions, writingItemAt: URL, options: NSFileCoordinator.WritingOptions, error: NSErrorPointer, byAccessor: (URL, URL) -> Void)

Initiates a read operation that contains a follow-up write operation.

func coordinate(writingItemAt: URL, options: NSFileCoordinator.WritingOptions, writingItemAt: URL, options: NSFileCoordinator.WritingOptions, error: NSErrorPointer, byAccessor: (URL, URL) -> Void)

Initiates a write operation that involves a secondary write operation.

func item(at: URL, willMoveTo: URL)

Announces that your app is moving a file to a new URL.

func item(at: URL, didMoveTo: URL)

Notifies relevant file presenters that the location of a file or directory changed.

func cancel()

Cancels any active file coordination calls.

