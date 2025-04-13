

- Core Foundation
-  CFArraySortValues(\_:\_:\_:\_:) 

Function

# CFArraySortValues(\_:\_:\_:\_:)

Sorts the values in an array using a given comparison function.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
func CFArraySortValues(
    _ theArray: CFMutableArray!,
    _ range: CFRange,
    _ comparator: CFComparatorFunction!,
    _ context: UnsafeMutableRawPointer!
)
```

## Parameters 

`theArray`  

The array whose values are sorted.

`range`  

The range of values within `theArray` to sort. The range location or end point (defined by the location plus length minus 1) must not lie outside the index space of `theArray` (`0` to `N-1` inclusive, where `N` is the count of `theArray`). The range length must not be negative. The range may be empty (length 0).

`comparator`  

The function with the comparator function type signature that is used in the sort operation to compare the values in `theArray`. If this parameter is not a pointer to a function of the correct prototype, the behavior is undefined. If there are values in `theArray` that the `comparator` function does not expect or cannot properly compare, the behavior is undefined. The values in the range are sorted from least to greatest according to this function.

`context`  

A pointer-sized program-defined value, which is passed as the third parameter to the `comparator` function, but is otherwise unused by this function. If the context is not what is expected by the `comparator` function, the behavior is undefined.

## See Also

### CFMutableArray Miscellaneous Functions

func CFArrayAppendArray(CFMutableArray!, CFArray!, CFRange)

Adds the values from one array to another array.

func CFArrayAppendValue(CFMutableArray!, UnsafeRawPointer!)

Adds a value to an array giving it the new largest index.

func CFArrayCreateMutable(CFAllocator!, CFIndex, UnsafePointer&lt;CFArrayCallBacks>!) -> CFMutableArray!

Creates a new empty mutable array.

func CFArrayCreateMutableCopy(CFAllocator!, CFIndex, CFArray!) -> CFMutableArray!

Creates a new mutable array with the values from another array.

func CFArrayExchangeValuesAtIndices(CFMutableArray!, CFIndex, CFIndex)

Exchanges the values at two indices of an array.

func CFArrayInsertValueAtIndex(CFMutableArray!, CFIndex, UnsafeRawPointer!)

Inserts a value into an array at a given index.

func CFArrayRemoveAllValues(CFMutableArray!)

Removes all the values from an array, making it empty.

func CFArrayRemoveValueAtIndex(CFMutableArray!, CFIndex)

Removes the value at a given index from an array.

func CFArrayReplaceValues(CFMutableArray!, CFRange, UnsafeMutablePointer&lt;UnsafeRawPointer?>!, CFIndex)

Replaces a range of values in an array.

func CFArraySetValueAtIndex(CFMutableArray!, CFIndex, UnsafeRawPointer!)

Changes the value at a given index in an array.

