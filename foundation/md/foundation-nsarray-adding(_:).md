

- Foundation
- NSArray
-  adding(\_:) 

Instance Method

# adding(\_:)

Returns a new array that is a copy of the receiving array with a given object added to the end.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func adding(_ anObject: Any) -> [Any]
```

## Parameters 

`anObject`  

An object.

## Return Value

A new array that is a copy of the receiving array with `anObject` added to the end.

## Discussion

If `anObject` is `nil`, an `NSInvalidArgumentException` is raised.

## See Also

### Related Documentation

func add(Any)

Inserts a given object at the end of the array.

### Deriving New Arrays

func addingObjects(from: [Any]) -> [Any]

Returns a new array that is a copy of the receiving array with the objects contained in another array added to the end.

func filtered(using: NSPredicate) -> [Any]

Evaluates a given predicate against each object in the receiving array and returns a new array containing the objects for which the predicate returns true.

func subarray(with: NSRange) -> [Any]

Returns a new array containing the receiving array’s elements that fall within the limits specified by a given range.

