

- Foundation
- NSFileCoordinator
- NSFileCoordinator.WritingOptions
-  forMoving 

Type Property

# forMoving

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
static var forMoving: NSFileCoordinator.WritingOptions { get }
```

## Discussion

When specified for a directory item, the file coordinator waits for already running read and write operations of the directory’s contents, which were themselves initiated through a file coordinator, to finish before moving the directory. Queued, but not executing, read and write operations on the directory’s contents wait until the move operation finishes.

This option has no effect on files. You can safely use it when moving file-system items without checking to see whether those items are files or directories.

## See Also

### Constants

static var forDeleting: NSFileCoordinator.WritingOptions

static var forMerging: NSFileCoordinator.WritingOptions

static var forReplacing: NSFileCoordinator.WritingOptions

static var contentIndependentMetadataOnly: NSFileCoordinator.WritingOptions

Select this option when writing to change the file’s metadata only and not its contents.

