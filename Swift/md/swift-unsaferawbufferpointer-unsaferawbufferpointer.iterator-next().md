

- Swift
- UnsafeRawBufferPointer
- UnsafeRawBufferPointer.Iterator
-  next() 

Instance Method

# next()

Advances to the next byte and returns it, or `nil` if no next byte exists.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
mutating func next() -> UInt8?
```

## Return Value

The next sequential byte in the raw buffer if another byte exists; otherwise, `nil`.

## Discussion

Once `nil` has been returned, all subsequent calls return `nil`.

