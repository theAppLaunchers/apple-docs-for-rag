

- Swift
- MemoryLayout
-  alignment 

Type Property

# alignment

The default memory alignment of `T`, in bytes.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
static var alignment: Int { get }
```

## Discussion

Use the `alignment` property for a type when allocating memory using an unsafe pointer. This value is always positive.

## See Also

### Accessing the Layout of a Type

static var size: Int

The contiguous memory footprint of `T`, in bytes.

static var stride: Int

The number of bytes from the start of one instance of `T` to the start of the next when stored in contiguous memory or in an `Array`.

