

- Foundation
- NSCompoundPredicate
-  init(coder:) 

Initializer

# init(coder:)

Creates a predicate by decoding from the coder you specify.

iOS 3.0+iPadOS 3.0+Mac Catalyst 13.1+macOS 10.4+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
init?(coder: NSCoder)
```

## Parameters 

`coder`  

The coder to read data from.

## See Also

### Creating Compound Predicates

init(andPredicateWithSubpredicates: [NSPredicate])

Returns a new predicate that you form using an AND operation on the predicates in a specified array.

init(notPredicateWithSubpredicate: NSPredicate)

Returns a new predicate that you form using a NOT operation on a specified predicate.

init(orPredicateWithSubpredicates: [NSPredicate])

Returns a new predicate that you form using an OR operation on the predicates in a specified array.

init(type: NSCompoundPredicate.LogicalType, subpredicates: [NSPredicate])

Returns the receiver that a specified type initializes using predicates from a specified array.

