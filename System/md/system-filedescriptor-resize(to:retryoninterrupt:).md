

- System
- FileDescriptor
-  resize(to:retryOnInterrupt:) 

Instance Method

# resize(to:retryOnInterrupt:)

Truncates or extends the file referenced by this file descriptor.

iOS 17.4+iPadOS 17.4+Mac Catalyst 17.4+macOS 14.4+tvOS 17.4+visionOS 1.0+watchOS 10.4+

``` source
func resize(
    to newSize: Int64,
    retryOnInterrupt: Bool = true
) throws
```

## Parameters 

`newSize`  

The length in bytes to resize the file to.

`retryOnInterrupt`  

Whether to retry the write operation if it throws interrupted. The default is `true`. Pass `false` to try only once and throw an error upon interruption.

## Discussion

The file referenced by this file descriptor will by truncated (or extended) to `newSize`.

If the current size of the file exceeds `newSize`, any extra data is discarded. If the current size of the file is smaller than `newSize`, the file is extended and filled with zeros to the provided size.

This function requires that the file has been opened for writing.

Note

This function does not modify the current offset for any open file descriptors associated with the file.

The corresponding C function is `ftruncate`.

