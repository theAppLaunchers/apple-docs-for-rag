

- Foundation
- NSMutableArray
-  insert(\_:at:) 

Instance Method

# insert(\_:at:)

Inserts a given object into the array’s contents at a given index.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func insert(
    _ anObject: Any,
    at index: Int
)
```

## Parameters 

`anObject`  

The object to add to the array’s content. This value must not be `nil`.

Important

Raises an `NSInvalidArgumentException` if `anObject` is `nil`.

`index`  

The index in the array at which to insert `anObject`. This value must not be greater than the count of elements in the array.

Important

Raises an `NSRangeException` if `index` is greater than the number of elements in the array.

## Discussion

If `index` is already occupied, the objects at `index` and beyond are shifted by adding `1` to their indices to make room.

Note that `NSArray` objects are not like C arrays. That is, even though you specify a size when you create an array, the specified size is regarded as a “hint”; the actual size of the array is still 0. This means that you cannot insert an object at an index greater than the current count of an array. For example, if an array contains two objects, its size is 2, so you can add objects at indices 0, 1, or 2. Index 3 is illegal and out of bounds; if you try to add an object at index 3 (when the size of the array is 2), `NSMutableArray` raises an exception.

## See Also

### Related Documentation

func removeObject(at: Int)

Removes the object at `index` .

### Adding Objects

func add(Any)

Inserts a given object at the end of the array.

func addObjects(from: [Any])

Adds the objects contained in another given array to the end of the receiving array’s content.

func insert([Any], at: IndexSet)

Inserts the objects in the provided array into the receiving array at the specified indexes.

