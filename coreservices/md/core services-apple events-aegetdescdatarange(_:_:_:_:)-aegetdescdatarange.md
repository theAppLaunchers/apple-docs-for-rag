

- Core Services
- Apple Events
-  AEGetDescDataRange(\_:\_:\_:\_:) 

Function

# AEGetDescDataRange(\_:\_:\_:\_:)

Retrieves a specified series of bytes from the specified descriptor.

macOS 10.2+

``` source
func AEGetDescDataRange(
    _ dataDesc: UnsafePointer!,
    _ buffer: UnsafeMutableRawPointer!,
    _ offset: Size,
    _ length: Size
) -> OSStatus
```

## Parameters 

`dataDesc`  

A pointer to the descriptor to get the data from. See AEDesc.

`buffer`  

A pointer to a buffer, local variable, or other storage location created and disposed of by your application. The size in bytes should be at least as large as the value you pass in the `length` parameter. On return, contains the specified data from the descriptor.

`offset`  

The zero-based offset to the data to be retrieved from the descriptor.

`length`  

The number of bytes of contiguous data to retrieve.

## Return Value

A result code. If the requested `offset` and `length` are such that they do not fit entirely within the descriptor’s data, `AEGetDescDataRange` returns `errAEBufferTooSmall`. See also Result Codes.

## Discussion

This function is valid only for value type descriptors (such as`typeUTF8Text`). You can use this function when you know the precise location of a subset of data within the descriptor. For example, if the descriptor contains a block of your private data, you might retrieve just a particular chunk you need at a known offset, representing an image, a string, or some other data type. Or if a descriptor contains an RGB color, you can access just the blue field.

When used in conjunction with AECreateDescFromExternalPtr(_:_:_:_:_:_:), `AEGetDescDataRange` can provide greatly improved performance, especially when working with large blocks of data.

## See Also

### Operating On Descriptor Data

func AEGetDescData(UnsafePointer&lt;AEDesc>!, UnsafeMutableRawPointer!, Size) -> OSErr

Gets the data from the specified descriptor.

func AEGetDescDataSize(UnsafePointer&lt;AEDesc>!) -> Size

Gets the size, in bytes, of the data in the specified descriptor.

func AEReplaceDescData(DescType, UnsafeRawPointer!, Size, UnsafeMutablePointer&lt;AEDesc>!) -> OSErr

Copies the specified data into the specified descriptor, replacing any previous data.

