

- Core Foundation
- CFBinaryHeapCallBacks
-  copyDescription 

Instance Property

# copyDescription

Callback function used to get a description of a value in a binary heap.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
var copyDescription: ((UnsafeRawPointer?) -> Unmanaged?)!
```

## Parameters 

`ptr`  

The value to be described.

## Discussion

The callback used to create a descriptive string representation of each value in the binary heap. This is used by the CFCopyDescription(_:) function. If this field is `NULL`, the binary heap constructs a `CFString` object describing the value based on its pointer value.

## See Also

### Callbacks

typealias CFBinaryHeapApplierFunction

Callback function used to apply a function to all members of a binary heap.

var compare: ((UnsafeRawPointer?, UnsafeRawPointer?, UnsafeMutableRawPointer?) -> CFComparisonResult)!

The callback used to compare values in the binary heap in some operations. This field cannot be `NULL`.

var release: ((CFAllocator?, UnsafeRawPointer?) -> Void)!

Callback function used to release a value before it is removed from a binary heap.

var retain: ((CFAllocator?, UnsafeRawPointer?) -> UnsafeRawPointer?)!

Callback function used to retain a value being added to a binary heap.

var version: CFIndex

The version number of the structure type being passed in as a parameter to the `CFBinaryHeap` creation functions. This structure is version `0`.

