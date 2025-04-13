

- Foundation
- NSArray
-  sortedArray(using:) 

Instance Method

# sortedArray(using:)

Returns an array that lists the receiving array’s elements in ascending order, as determined by the comparison method specified by a given selector.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func sortedArray(using comparator: Selector) -> [Any]
```

## Parameters 

`comparator`  

A selector that identifies the method to use to compare two elements at a time. The method should return `NSOrderedAscending` if the receiving array is smaller than the argument, `NSOrderedDescending` if the receiving array is larger than the argument, and `NSOrderedSame` if they are equal.

## Return Value

An array that lists the receiving array’s elements in ascending order, as determined by the comparison method specified by the selector `comparator`.

## Discussion

The new array contains references to the receiving array’s elements, not copies of them.

The `comparator` message is sent to each object in the array and has as its single argument another object in the array.

For example, an array of `NSString` objects can be sorted by using the caseInsensitiveCompare(_:) method declared in the `NSString` class. Assuming `anArray` exists, a sorted version of the array can be created in this way:

```
     NSArray *sortedArray =
         [anArray sortedArrayUsingSelector:@selector(caseInsensitiveCompare:)];
```

## See Also

### Sorting

var sortedArrayHint: Data

Analyzes the array and returns a “hint” that speeds the sorting of the array when the hint is supplied to sortedArray(_:context:hint:).

func sortedArray((Any, Any, UnsafeMutableRawPointer?) -> Int, context: UnsafeMutableRawPointer?) -> [Any]

Returns a new array that lists the receiving array’s elements in ascending order as defined by the comparison function `comparator`.

func sortedArray((Any, Any, UnsafeMutableRawPointer?) -> Int, context: UnsafeMutableRawPointer?, hint: Data?) -> [Any]

Returns a new array that lists the receiving array’s elements in ascending order as defined by the comparison function `comparator`.

func sortedArray(using: [NSSortDescriptor]) -> [Any]

Returns a copy of the receiving array sorted as specified by a given array of sort descriptors.

func sortedArray(comparator: (Any, Any) -> ComparisonResult) -> [Any]

Returns an array that lists the receiving array’s elements in ascending order, as determined by the comparison method specified by a given `NSComparator` block.

func sortedArray(options: NSSortOptions, usingComparator: (Any, Any) -> ComparisonResult) -> [Any]

Returns an array that lists the receiving array’s elements in ascending order, as determined by the comparison method specified by a given `NSComparator` block.

typealias Comparator

Defines the signature for a block object used for comparison operations.

