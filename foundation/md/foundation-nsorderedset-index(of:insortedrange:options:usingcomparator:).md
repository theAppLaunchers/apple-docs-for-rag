

- Foundation
- NSOrderedSet
-  index(of:inSortedRange:options:usingComparator:) 

Instance Method

# index(of:inSortedRange:options:usingComparator:)

Returns the index, within a specified range, of an object compared with elements in the ordered set using a given NSComparator block.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func index(
    of object: Any,
    inSortedRange range: NSRange,
    options opts: NSBinarySearchingOptions = [],
    usingComparator cmp: (Any, Any) -> ComparisonResult
) -> Int
```

## Parameters 

`object`  

An object for which to search in the ordered set.

If this value is `nil`, throws an invalidArgumentException.

`range`  

The range within the array to search for `object`.

If r exceeds the bounds of the ordered set (if the location plus length of the range is greater than the count of the ordered set), throws an rangeException.

`opts`  

Options for the search. For possible values, see NSBinarySearchingOptions.

`cmp`  

A comparator block used to compare the object obj with elements in the ordered set.

If this value is `NULL`, throws an invalidArgumentException.

## Return Value

If the insertionIndex option is not specified:

- If the `object` is found and neither firstEqual nor lastEqual is specified, returns the matching object’s index.

- If the firstEqual or lastEqual option is also specified, returns the index of equal objects.

- If the object is not found, returns `NSNotFound`.

If the insertionIndex option is specified, returns the index at which you should insert `obj` in order to maintain a sorted array:

- If the `object` is found and neither firstEqual nor lastEqual is specified, returns the matching object’s index.

- If the firstEqual or lastEqual option is also specified, returns the index of the equal objects.

- If the object is not found, returns the index of the least greater object, or the index at the end of the array if the object is larger than all other elements.

## Discussion

The elements in the ordered set must have already been sorted using the comparator `cmp`. If the ordered set is not sorted, the result is undefined.

## See Also

### Accessing Set Members

func contains(Any) -> Bool

Returns a Boolean value that indicates whether a given object is present in the ordered set.

func enumerateObjects(at: IndexSet, options: NSEnumerationOptions, using: (Any, Int, UnsafeMutablePointer&lt;ObjCBool>) -> Void)

Executes a given block using the objects in the ordered set at the specified indexes.

func enumerateObjects((Any, Int, UnsafeMutablePointer&lt;ObjCBool>) -> Void)

Executes a given block using each object in the ordered set.

func enumerateObjects(options: NSEnumerationOptions, using: (Any, Int, UnsafeMutablePointer&lt;ObjCBool>) -> Void)

Executes a given block using each object in the set, using the specified enumeration options.

var firstObject: Any?

The first object in the ordered set.

var lastObject: Any?

The last object in the ordered set.

func object(at: Int) -> Any

Returns the object at the specified index of the set.

func objects(at: IndexSet) -> [Any]

Returns the objects in the ordered set at the specified indexes.

func index(of: Any) -> Int

Returns the index of the specified object.

func index(ofObjectAt: IndexSet, options: NSEnumerationOptions, passingTest: (Any, Int, UnsafeMutablePointer&lt;ObjCBool>) -> Bool) -> Int

Returns the index, from a given set of indexes, of the object in the ordered set that passes a test in a given block for a given set of enumeration options.

func index(ofObjectPassingTest: (Any, Int, UnsafeMutablePointer&lt;ObjCBool>) -> Bool) -> Int

Returns the index of the object in the ordered set that passes a test in a given block.

func index(NSEnumerationOptions, ofObjectPassingTest: (Any, Int, UnsafeMutablePointer&lt;ObjCBool>) -> Bool) -> Int

Returns the index of an object in the ordered set that passes a test in a given block for a given set of enumeration options.

func indexes(ofObjectsAt: IndexSet, options: NSEnumerationOptions, passingTest: (Any, Int, UnsafeMutablePointer&lt;ObjCBool>) -> Bool) -> IndexSet

Returns the index, from a given set of indexes, of the object in the ordered set that passes a test in a given block for a given set of enumeration options.

func indexes(ofObjectsPassingTest: (Any, Int, UnsafeMutablePointer&lt;ObjCBool>) -> Bool) -> IndexSet

Returns the index of the object in the ordered set that passes a test in a given block.

func indexes(options: NSEnumerationOptions, ofObjectsPassingTest: (Any, Int, UnsafeMutablePointer&lt;ObjCBool>) -> Bool) -> IndexSet

Returns the index of an object in the ordered set that passes a test in a given block for a given set of enumeration options.

