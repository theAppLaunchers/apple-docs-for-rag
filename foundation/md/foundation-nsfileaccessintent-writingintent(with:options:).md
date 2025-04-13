

- Foundation
- NSFileAccessIntent
-  writingIntent(with:options:) 

Type Method

# writingIntent(with:options:)

Returns a file access intent object for writing to the given URL with the provided options.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
class func writingIntent(
    with url: URL,
    options: NSFileCoordinator.WritingOptions = []
) -> Self
```

## Parameters 

`url`  

The URL of the document you intend to write to.

`options`  

The coordinated writing options. For a list of valid values, see NSFileCoordinator.WritingOptions in the NSFileCoordinator.

## Return Value

A newly instantiated and configured file access intent object.

## Discussion

When calling a file coordinator’s coordinate(with:queue:byAccessor:) method, you pass an array of file access intent objects. Each intent object represents a specific read or write operation on a single document or directory. Use `writingIntentWithURL:options:` to create an intent object suitable for writing.

## See Also

### Related Documentation

func coordinate(with: [NSFileAccessIntent], queue: OperationQueue, byAccessor: ((any Error)?) -> Void)

Performs a number of coordinated-read or -write operations asynchronously.

### Creating a File Access Intent

class func readingIntent(with: URL, options: NSFileCoordinator.ReadingOptions) -> Self

Returns a file access intent object for reading the given URL with the provided options.

