

- Swift
- UnsafeMutableBufferPointer
-  allocate(capacity:) 

Type Method

# allocate(capacity:)

Allocates uninitialized memory for the specified number of instances of type `Element`.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
static func allocate(capacity count: Int) -> UnsafeMutableBufferPointer
```

## Parameters 

`count`  

The amount of memory to allocate, counted in instances of `Element`.

## Discussion

The resulting buffer references a region of memory that is bound to `Element` and is `count * MemoryLayout.stride` bytes in size.

The following example allocates a buffer that can store four `Int` instances and then initializes that memory with the elements of a range:

```
let buffer = UnsafeMutableBufferPointer.allocate(capacity: 4)
_ = buffer.initialize(from: 1...4)
print(buffer[2])
// Prints "3"
```

When you allocate memory, always remember to deallocate once you’re finished.

```
buffer.deallocate()
```

