

- Foundation
- NSExpression
-  init(forAggregate:) 

Initializer

# init(forAggregate:)

Creates an aggregate expression for a specified collection.

iOS 3.0+iPadOS 3.0+Mac Catalyst 13.1+macOS 10.5+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
init(forAggregate subexpressions: [NSExpression])
```

## Parameters 

`subexpressions`  

A collection object (an instance of `NSArray`, `NSSet`, or `NSDictionary`) that contains further expressions.

## Return Value

A new expression that contains the expressions in `collection`.

## See Also

### Creating a Collection Expression

init(forUnionSet: NSExpression, with: NSExpression)

Creates an expression object that represents the union of a specified set and collection.

init(forIntersectSet: NSExpression, with: NSExpression)

Creates an expression object that represents the intersection of a specified set and collection.

init(forMinusSet: NSExpression, with: NSExpression)

Creates an expression object that represents the subtraction of a specified collection from a specified set.

