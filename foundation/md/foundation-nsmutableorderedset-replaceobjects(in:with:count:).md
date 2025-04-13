

- Foundation
- NSMutableOrderedSet
-  replaceObjects(in:with:count:) 

Instance Method

# replaceObjects(in:with:count:)

Replaces the objects in the receiving mutable ordered set at the range with the specified number of objects from a given C array.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func replaceObjects(
    in range: NSRange,
    with objects: UnsafePointer?,
    count: Int
)
```

## Parameters 

`range`  

The range of the objects to replace.

`objects`  

A C array of objects.

`count`  

The number of values from the objects C array to insert in place of the objects in `range`. This number will be the count of the new array—it must not be negative or greater than the number of elements in objects.

## Discussion

Elements are added to the new array in the same order they appear in objects, up to but not including index count.

## See Also

### Adding, Removing, and Reordering Entries

func add(Any)

Appends a given object to the end of the mutable ordered set, if it is not already a member.

func add(UnsafePointer&lt;AnyObject>?, count: Int)

Appends the given number of objects from a given C array to the end of the mutable ordered set.

func addObjects(from: [Any])

Appends to the end of the mutable ordered set each object contained in a given array that is not already a member.

func insert(Any, at: Int)

Inserts the given object at the specified index of the mutable ordered set, if it is not already a member.

func insert([Any], at: IndexSet)

Inserts the objects in the array at the specified indexes.

func remove(Any)

Removes a given object from the mutable ordered set.

func removeObject(at: Int)

Removes a the object at the specified index from the mutable ordered set.

func removeObjects(at: IndexSet)

Removes the objects at the specified indexes from the mutable ordered set.

func removeObjects(in: [Any])

Removes the objects in the array from the mutable ordered set.

func removeObjects(in: NSRange)

Removes from the mutable ordered set each of the objects within a given range.

func removeAllObjects()

Removes all the objects from the mutable ordered set.

func replaceObject(at: Int, with: Any)

Replaces the object at the specified index with the new object.

func replaceObjects(at: IndexSet, with: [Any])

Replaces the objects at the specified indexes with the new objects.

func setObject(Any, at: Int)

Appends or replaces the object at the specified index.

func moveObjects(at: IndexSet, to: Int)

Moves the objects at the specified indexes to the new location.

