

- Core Foundation
-  CFArrayAppendValue(\_:\_:) 

Function

# CFArrayAppendValue(\_:\_:)

Adds a value to an array giving it the new largest index.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
func CFArrayAppendValue(
    _ theArray: CFMutableArray!,
    _ value: UnsafeRawPointer!
)
```

## Parameters 

`theArray`  

The array to which `value` is to be added. If `theArray` is a limited-capacity array and it is full before this operation, the behavior is undefined.

`value`  

A CFType object or a pointer value to add to `theArray`.

## Discussion

The `value` parameter is retained by `theArray` using the retain callback provided when `theArray` was created. If `value` is not of the type expected by the retain callback, the behavior is undefined. The `value` parameter is assigned to the index one larger than the previous largest index and the count of `theArray` is increased by one.

## See Also

### CFMutableArray Miscellaneous Functions

func CFArrayAppendArray(CFMutableArray!, CFArray!, CFRange)

Adds the values from one array to another array.

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

func CFArraySortValues(CFMutableArray!, CFRange, CFComparatorFunction!, UnsafeMutableRawPointer!)

Sorts the values in an array using a given comparison function.

