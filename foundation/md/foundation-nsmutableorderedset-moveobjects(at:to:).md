

- Foundation
- NSMutableOrderedSet
-  moveObjects(at:to:) 

Instance Method

# moveObjects(at:to:)

Moves the objects at the specified indexes to the new location.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func moveObjects(
    at indexes: IndexSet,
    to idx: Int
)
```

## Parameters 

`indexes`  

The indexes of the objects to move.

`idx`  

The index in the mutable ordered set at which to insert the objects. The objects being moved are first removed from the set, then this index is used to find the location at which to insert the moved objects.

## Discussion

For example, the following code results in the contents of `mySet` being equal to `["a", "c", "b", "d", "e"]:`

- Swift
- Objective-C

```
let movedObjectIndexes = NSMutableIndexSet()
movedObjectIndexes.addIndex(1)
movedObjectIndexes.addIndex(3)

let mySet = NSMutableOrderedSet(capacity: 5)
mySet.addObject("a")
mySet.addObject("b")
mySet.addObject("c")
mySet.addObject("d")
mySet.addObject("e")

mySet.moveObjectsAtIndexes(movedObjectIndexes, toIndex: 2)
```

```
NSMutableIndexSet *movedObjectIndexes = [NSMutableIndexSet indexSet];
[movedObjectIndexes addIndex: 1];
[movedObjectIndexes addIndex: 3];

NSMutableOrderedSet *mySet = [NSMutableOrderedSet orderedSetWithCapacity:5];
[mySet addObject:@"a"];
[mySet addObject:@"b"];
[mySet addObject:@"c"];
[mySet addObject:@"d"];
[mySet addObject:@"e"];

[mySet moveObjectsAtIndexes:movedObjectIndexes toIndex:2];
```

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

func replaceObjects(in: NSRange, with: UnsafePointer&lt;AnyObject>?, count: Int)

Replaces the objects in the receiving mutable ordered set at the range with the specified number of objects from a given C array.

func setObject(Any, at: Int)

Appends or replaces the object at the specified index.

