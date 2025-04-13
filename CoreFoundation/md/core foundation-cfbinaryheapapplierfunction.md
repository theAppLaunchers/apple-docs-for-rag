

- Core Foundation
-  CFBinaryHeapApplierFunction 

Type Alias

# CFBinaryHeapApplierFunction

Callback function used to apply a function to all members of a binary heap.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
typealias CFBinaryHeapApplierFunction = (UnsafeRawPointer?, UnsafeMutableRawPointer?) -> Void
```

## Parameters 

`val`  

The current value from the binary heap.

`context`  

The program-defined context parameter given to the CFBinaryHeapApplyFunction(_:_:_:) function.

## See Also

### Callbacks

var compare: ((UnsafeRawPointer?, UnsafeRawPointer?, UnsafeMutableRawPointer?) -> CFComparisonResult)!

The callback used to compare values in the binary heap in some operations. This field cannot be `NULL`.

var copyDescription: ((UnsafeRawPointer?) -> Unmanaged&lt;CFString>?)!

Callback function used to get a description of a value in a binary heap.

var release: ((CFAllocator?, UnsafeRawPointer?) -> Void)!

Callback function used to release a value before it is removed from a binary heap.

var retain: ((CFAllocator?, UnsafeRawPointer?) -> UnsafeRawPointer?)!

Callback function used to retain a value being added to a binary heap.

var version: CFIndex

The version number of the structure type being passed in as a parameter to the `CFBinaryHeap` creation functions. This structure is version `0`.

