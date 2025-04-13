

- Foundation
- NSMutableOrderedSet
-  insert(\_:at:) 

Instance Method

# insert(\_:at:)

Inserts the given object at the specified index of the mutable ordered set, if it is not already a member.

iOS 5.0+iPadOS 5.0+Mac Catalyst 13.1+macOS 10.7+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func insert(
    _ object: Any,
    at idx: Int
)
```

## Parameters 

`object`  

The object to insert into the set’s content.

`idx`  

The index in the mutable ordered set at which to insert `object`. This value must not be greater than the count of elements in the array.

Important

Important: Raises an rangeException if `idx` is greater than the number of elements in the mutable ordered set.

## Discussion

If the object is already a member, this method has no effect. If the specified index is already occupied, the objects at that index and beyond are shifted by adding `1` to their indexes to make room for the inserted object.

## See Also

### Adding, Removing, and Reordering Entries

func add(Any)

Appends a given object to the end of the mutable ordered set, if it is not already a member.

func add(UnsafePointer&lt;AnyObject>?, count: Int)

Appends the given number of objects from a given C array to the end of the mutable ordered set.

func addObjects(from: [Any])

Appends to the end of the mutable ordered set each object contained in a given array that is not already a member.

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

func replaceObjects(in: NSRange, with: UnsafePointer&lt;AnyObject>?, count: Int)

Replaces the objects in the receiving mutable ordered set at the range with the specified number of objects from a given C array.

func setObject(Any, at: Int)

Appends or replaces the object at the specified index.

func moveObjects(at: IndexSet, to: Int)

Moves the objects at the specified indexes to the new location.

