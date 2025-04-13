

- Swift
- SetAlgebra
-  isSubset(of:) 

Instance Method

# isSubset(of:)

Returns a Boolean value that indicates whether the set is a subset of another set.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func isSubset(of other: Self) -> Bool
```

**Required** Default implementation provided.

## Parameters 

`other`  

A set of the same type as the current set.

## Return Value

`true` if the set is a subset of `other`; otherwise, `false`.

## Discussion

Set *A* is a subset of another set *B* if every member of *A* is also a member of *B*.

```
let employees: Set = ["Alicia", "Bethany", "Chris", "Diana", "Eric"]
let attendees: Set = ["Alicia", "Bethany", "Diana"]
print(attendees.isSubset(of: employees))
// Prints "true"
```

## Default Implementations

### SetAlgebra Implementations

func isSubset(of: Self) -> Bool

Returns a Boolean value that indicates whether the set is a subset of another set.

