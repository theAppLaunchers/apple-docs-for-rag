

- Swift
- UnsafeMutablePointer
-  initialize(to:) 

Instance Method

# initialize(to:)

Initializes this pointer’s memory with a single instance of the given value.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func initialize(to value: consuming Pointee)
```

## Parameters 

`value`  

The instance to initialize this pointer’s pointee to.

## Discussion

The destination memory must be uninitialized or the pointer’s `Pointee` must be a trivial type. After a call to `initialize(to:)`, the memory referenced by this pointer is initialized. Calling this method is roughly equivalent to calling `initialize(repeating:count:)` with a `count` of 1.

