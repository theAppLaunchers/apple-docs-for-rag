

- Foundation
- NSHashTable
-  anyObject 

Instance Property

# anyObject

One of the objects in the hash table.

iOS 6.0+iPadOS 6.0+Mac Catalyst 13.1+macOS 10.5+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var anyObject: ObjectType? { get }
```

## Discussion

One of the objects in the hash table, or `nil` if the hash table contains no objects.

The object returned is chosen at the hash table’s convenience—the selection is not guaranteed to be random.

## See Also

### Accessing Content

var allObjects: [ObjectType]

The hash table’s members.

var setRepresentation: Set&lt;AnyHashable>

A set that contains the hash table’s members.

var count: Int

The number of elements in the hash table.

func contains(ObjectType?) -> Bool

Returns a Boolean value that indicates whether the hash table contains a given object.

func member(ObjectType?) -> ObjectType?

Determines whether the hash table contains a given object, and returns that object if it is present

func objectEnumerator() -> NSEnumerator

Returns an enumerator object that lets you access each object in the hash table.

