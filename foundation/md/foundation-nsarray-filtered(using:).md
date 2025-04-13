

- Foundation
- NSArray
-  filtered(using:) 

Instance Method

# filtered(using:)

Evaluates a given predicate against each object in the receiving array and returns a new array containing the objects for which the predicate returns true.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func filtered(using predicate: NSPredicate) -> [Any]
```

## Parameters 

`predicate`  

The predicate against which to evaluate the receiving array’s elements.

## Return Value

A new array containing the objects in the receiving array for which `predicate` returns true.

Objects in the resulting array appear in the same order as they do in the receiver.

## Discussion

For more details, see Predicate Programming Guide.

## See Also

### Deriving New Arrays

func adding(Any) -> [Any]

Returns a new array that is a copy of the receiving array with a given object added to the end.

func addingObjects(from: [Any]) -> [Any]

Returns a new array that is a copy of the receiving array with the objects contained in another array added to the end.

func subarray(with: NSRange) -> [Any]

Returns a new array containing the receiving array’s elements that fall within the limits specified by a given range.

