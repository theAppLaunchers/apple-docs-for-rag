

- Foundation
- NSFileCoordinator
- NSFileCoordinator.ReadingOptions
-  forUploading 

Type Property

# forUploading

Specify this content when reading an item for the purpose of uploading its contents.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
static var forUploading: NSFileCoordinator.ReadingOptions { get }
```

## Discussion

When this option is used, the file coordinator creates a temporary snapshot of the item being read and relinquishes its claim on the original file. This action prevents the read operation from blocking other coordinated writes during a potentially long upload.

If the item being read is a directory (such as a document package), then the snapshot is a new file containing the zipped contents of the directory. The URL passed to the accessor block points to the zipped file.

When using this option, you may upload the document outside the accessor block. However, you should open a file descriptor to the file or relocate the file within the accessor block before doing so. The file coordinator unlinks the file after the block returns, rendering it inaccessible through the URL.

## See Also

### Constants

static var withoutChanges: NSFileCoordinator.ReadingOptions

static var resolvesSymbolicLink: NSFileCoordinator.ReadingOptions

static var immediatelyAvailableMetadataOnly: NSFileCoordinator.ReadingOptions

Specify this constant if you want to read an item’s metadata without triggering a download.

