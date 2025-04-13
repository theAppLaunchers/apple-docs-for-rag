

- Foundation
- FileHandle
-  synchronize() 

Instance Method

# synchronize()

Causes all in-memory data and attributes of the file represented by the file handle to write to permanent storage.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
func synchronize() throws
```

## Discussion

Programs that require the file to always be in a known state should call this method. An invocation of this method doesn’t return until memory is flushed.

## See Also

### Operating on a File

func close() throws

Disallows further access to the represented file or communications channel and signals end of file on communications channels that permit writing.

func truncate(atOffset: UInt64) throws

Truncates or extends the file represented by the file handle to a specified offset within the file and puts the file pointer at that position.

