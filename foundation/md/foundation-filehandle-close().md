

- Foundation
- FileHandle
-  close() 

Instance Method

# close()

Disallows further access to the represented file or communications channel and signals end of file on communications channels that permit writing.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
func close() throws
```

## Discussion

If the file handle object owns its file descriptor, it automatically closes that descriptor when deallocated. If you initialized the file handle object using the init(fileDescriptor:) method, or you initialized it using the init(fileDescriptor:closeOnDealloc:) and passed false for the `flag` parameter, you can use this method to close the file descriptor; otherwise, you must close the file descriptor yourself.

After calling this method, you may still use the file handle object, but you must not attempt to read or write data or use the object to operate on the file descriptor. Attempts to read or write a closed file descriptor raise an exception.

## See Also

### Operating on a File

func synchronize() throws

Causes all in-memory data and attributes of the file represented by the file handle to write to permanent storage.

func truncate(atOffset: UInt64) throws

Truncates or extends the file represented by the file handle to a specified offset within the file and puts the file pointer at that position.

