

- Contacts
- CNContactStore
-  groups(matching:) 

Instance Method

# groups(matching:)

Fetches all groups matching the specified predicate.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+visionOS 1.0+watchOS 2.0+

``` source
func groups(matching predicate: NSPredicate?) throws -> [CNGroup]
```

## Parameters 

`predicate`  

The predicate to use to fetch the matching groups. Set predicate to `nil` to match all groups.

## Return Value

An array of CNGroup objects that match the predicate.

## Discussion

This method returns an empty array when no matching groups are found. If an error occurs, this method returns `nil`. You should use only the predicates defined in CNGroup class predicates. Compound predicates are not supported. Contacts may be members of one or more groups, depending upon the account they come from.

Handling Errors in Swift

In Swift, this method returns a nonoptional result and is marked with the `throws` keyword to indicate that it throws an error in cases of failure. You call this method in a `try` expression and handle any errors in the `catch` clauses of a `do` statement, as described in Error Handling in The Swift Programming Language and About Imported Cocoa Error Parameters.

## See Also

### Fetching groups and containers

func defaultContainerIdentifier() -> String

Returns the identifier of the default container.

func containers(matching: NSPredicate?) throws -> [CNContainer]

Fetches all containers matching the specified predicate.

