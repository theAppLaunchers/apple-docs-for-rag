

- Core Foundation
-  CFArrayExchangeValuesAtIndices(\_:\_:\_:) 

Function

# CFArrayExchangeValuesAtIndices(\_:\_:\_:)

Exchanges the values at two indices of an array.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
func CFArrayExchangeValuesAtIndices(
    _ theArray: CFMutableArray!,
    _ idx1: CFIndex,
    _ idx2: CFIndex
)
```

## Parameters 

`theArray`  

The array that contains the values to be swapped.

`idx1`  

The index of the value to swap with the value at `idx2`. The index must not exceed the index space of `theArray` (`0` to `N-1` inclusive, where `N` is the count of `theArray` before the operation).

`idx2`  

The index of the value to swap with the value at `idx1`. The index must not exceed the index space of `theArray` (`0` to `N-1` inclusive, where `N` is the count of `theArray` before the operation).

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

func CFArraySortValues(CFMutableArray!, CFRange, CFComparatorFunction!, UnsafeMutableRawPointer!)

Sorts the values in an array using a given comparison function.

