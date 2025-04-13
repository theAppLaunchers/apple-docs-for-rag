

- Swift
- MemoryLayout
-  size 

Type Property

# size

The contiguous memory footprint of `T`, in bytes.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
static var size: Int { get }
```

## Discussion

A type’s size does not include any dynamically allocated or out of line storage. In particular, `MemoryLayout.size`, when `T` is a class type, is the same regardless of how many stored properties `T` has.

When allocating memory for multiple instances of `T` using an unsafe pointer, use a multiple of the type’s stride instead of its size.

## See Also

### Accessing the Layout of a Type

static var alignment: Int

The default memory alignment of `T`, in bytes.

static var stride: Int

The number of bytes from the start of one instance of `T` to the start of the next when stored in contiguous memory or in an `Array`.

