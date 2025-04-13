

- Foundation
- Pipe
-  fileHandleForWriting 

Instance Property

# fileHandleForWriting

The receiver’s write file handle.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var fileHandleForWriting: FileHandle { get }
```

## Discussion

This object is automatically deallocated when the receiver is deallocated.

You use the returned file handle to write to the pipe using `NSFileHandle`’s write(_:) method. When you are finished writing data to this object, send it a closeFile() message to delete the descriptor. Deleting the descriptor causes the reading process to receive an end-of-data signal (an empty `NSData` object).

## See Also

### Getting the File Handles for a Pipe

var fileHandleForReading: FileHandle

The receiver’s read file handle.

