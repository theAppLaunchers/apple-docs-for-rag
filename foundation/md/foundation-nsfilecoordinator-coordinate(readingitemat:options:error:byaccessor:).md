

- Foundation
- NSFileCoordinator
-  coordinate(readingItemAt:options:error:byAccessor:) 

Instance Method

# coordinate(readingItemAt:options:error:byAccessor:)

Initiates a read operation on a single file or directory using the specified options.

iOS 5.0+iPadOS 5.0+Mac Catalyst 13.1+macOS 10.7+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func coordinate(
    readingItemAt url: URL,
    options: NSFileCoordinator.ReadingOptions = [],
    error outError: NSErrorPointer,
    byAccessor reader: (URL) -> Void
)
```

## Parameters 

`url`  

A URL identifying the file or directory to read. If other objects or processes are acting on the item at the URL, the actual URL passed to the `reader` parameter may be different than the one in this parameter.

`options`  

One of the reading options described in NSFileCoordinator.ReadingOptions. If you pass no options, the savePresentedItemChanges(completionHandler:) method of relevant file presenters is called before your block executes.

`outError`  

On input, a pointer to a pointer for an error object. If a file presenter encounters an error while preparing for this read operation, that error is returned in this parameter and the block in the `reader` parameter is not executed. If you cancel this operation before the `reader` block is executed, this parameter contains an error object on output.

`reader`  

A Block object containing the file operations you want to perform in a coordinated manner. This block receives an NSURL object containing the URL of the item and returns no value. Always use the URL passed into the block instead of the value in the `url` parameter.

## Discussion

You use this method to perform read-related operations on a file or directory in a coordinated manner. This method executes synchronously, blocking the current thread until the `reader` block finishes executing. Before executing that block, though, the file coordinator waits until other relevant file presenter objects finish in-progress actions. Similarly, your read operation may cause pending actions for other file presenters to wait until your operations are complete. Whether or not the file coordinator waits depends on whether the item being read is a file or a directory and also depends on other related operations.

- If the `url` parameter specifies a file:

- This method waits for other writers of the exact same file to finish in-progress actions.

- This method waits if the file is a file package or any item inside the file package and other writers are writing to other items in the package directory.

- This method does not wait for other readers of the file.

- This method does not wait for writers that are manipulating the parent directory of the file, unless one of those writers specified the forDeleting or forMoving option.

- If the `url` parameter specifies a directory:

- This method waits if other write operations are occurring on the exact same directory.

- This method does not wait if write operations are occurring on items inside the directory (but not on the directory itself).

- This method does not wait for other readers of the directory.

- This method does not wait for writers that are manipulating the parent directory of the directory, unless one of those writers specified the forDeleting or forMoving option.

When invoking these methods, declare a `__block` variable before the accessor block and initialize it to a value that signals failure, and then inside the accessor block set it to a value that indicates success. If the coordinated operation fails, then the accessor block never runs. The sentinel variable still holds a value that indicates failure, and the NSError out parameter contains a reference that describes the error.

This method calls the relinquishPresentedItem(toReader:) method of any relevant file presenters. This method is called for file presenters in the current process and in other processes. Depending on the options you specify, other methods of the file presenters may also be called. When reading a file package directory, file presenter objects that are currently reading the contents of that file package also receive these notifications. All of the called methods must return successfully before the file coordinator executes your block. If multiple file presenters are operating on the item, the order in which those presenters are notified is undefined.

If the device has not yet downloaded the file at the given URL, this method blocks (potentially for a long time) while the file is downloaded. If the file cannot be downloaded, this method fails. Alternatively; use a metadata query to check for the NSMetadataUbiquitousItemDownloadingStatusKey key, and then call the startDownloadingUbiquitousItem(at:) method to download the file before trying to read it.

If you want to perform a write operation from inside a read block, use the coordinate(writingItemAt:options:writingItemAt:options:error:byAccessor:) method.

If you want to perform a batch read operation on multiple files, use the prepare(forReadingItemsAt:options:writingItemsAt:options:error:byAccessor:) method instead.

## See Also

### Coordinating File Operations Synchronously

func coordinate(writingItemAt: URL, options: NSFileCoordinator.WritingOptions, error: NSErrorPointer, byAccessor: (URL) -> Void)

Initiates a write operation on a single file or directory using the specified options.

func coordinate(readingItemAt: URL, options: NSFileCoordinator.ReadingOptions, writingItemAt: URL, options: NSFileCoordinator.WritingOptions, error: NSErrorPointer, byAccessor: (URL, URL) -> Void)

Initiates a read operation that contains a follow-up write operation.

func coordinate(writingItemAt: URL, options: NSFileCoordinator.WritingOptions, writingItemAt: URL, options: NSFileCoordinator.WritingOptions, error: NSErrorPointer, byAccessor: (URL, URL) -> Void)

Initiates a write operation that involves a secondary write operation.

func prepare(forReadingItemsAt: [URL], options: NSFileCoordinator.ReadingOptions, writingItemsAt: [URL], options: NSFileCoordinator.WritingOptions, error: NSErrorPointer, byAccessor: (() -> Void) -> Void)

Prepare to read or write from multiple files in a single batch operation.

func item(at: URL, willMoveTo: URL)

Announces that your app is moving a file to a new URL.

func item(at: URL, didMoveTo: URL)

Notifies relevant file presenters that the location of a file or directory changed.

func cancel()

Cancels any active file coordination calls.

