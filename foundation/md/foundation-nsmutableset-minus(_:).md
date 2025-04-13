

- Foundation
- NSMutableSet
-  minus(\_:) 

Instance Method

# minus(\_:)

Removes each object in another given set from the receiving set, if present.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func minus(_ otherSet: Set)
```

## Parameters 

`otherSet`  

The set of objects to remove from the receiving set.

## See Also

### Related Documentation

func remove(Any)

Removes a given object from the set.

func removeAllObjects()

Empties the set of all of its members.

### Combining and recombining sets

func union(Set&lt;AnyHashable>)

Adds each object in another given set to the receiving set, if not present.

func intersect(Set&lt;AnyHashable>)

Removes from the receiving set each object that isn’t a member of another given set.

func setSet(Set&lt;AnyHashable>)

Empties the receiving set, then adds each object contained in another given set.

