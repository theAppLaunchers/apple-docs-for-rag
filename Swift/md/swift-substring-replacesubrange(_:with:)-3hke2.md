

- Swift
- Substring
-  replaceSubrange(\_:with:) 

Instance Method

# replaceSubrange(\_:with:)

Replaces the specified subrange of elements with the given collection.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
mutating func replaceSubrange(
    _ subrange: Range,
    with newElements: C
) where C : Collection, Self.Element == C.Element
```

## Parameters 

`subrange`  

The subrange of the collection to replace. The bounds of the range must be valid indices of the collection.

`newElements`  

The new elements to add to the collection.

## Discussion

This method has the effect of removing the specified range of elements from the collection and inserting the new elements at the same location. The number of new elements need not match the number of elements being removed.

In this example, three elements in the middle of an array of integers are replaced by the five elements of a `Repeated` instance.

```
 var nums = [10, 20, 30, 40, 50]
 nums.replaceSubrange(1...3, with: repeatElement(1, count: 5))
 print(nums)
 // Prints "[10, 1, 1, 1, 1, 1, 50]"
```

If you pass a zero-length range as the `subrange` parameter, this method inserts the elements of `newElements` at `subrange.startIndex`. Calling the `insert(contentsOf:at:)` method instead is preferred.

Likewise, if you pass a zero-length collection as the `newElements` parameter, this method removes the elements in the given subrange without replacement. Calling the `removeSubrange(_:)` method instead is preferred.

Calling this method may invalidate any existing indices for use with this collection.

Complexity

O(*n* + *m*), where *n* is length of this collection and *m* is the length of `newElements`. If the call to this method simply appends the contents of `newElements` to the collection, this method is equivalent to `append(contentsOf:)`.

