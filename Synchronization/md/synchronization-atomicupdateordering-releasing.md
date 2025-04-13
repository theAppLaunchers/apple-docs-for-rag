

- Synchronization
- AtomicUpdateOrdering
-  releasing 

Type Property

# releasing

A releasing update synchronizes with acquiring operations that read the value it stores. It ensures that the releasing and acquiring threads agree that all preceding variable accesses on the releasing thread happen before the atomic operation itself.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
static var releasing: AtomicUpdateOrdering { get }
```

## Discussion

This value corresponds to `std::memory_order_release` in C++.

