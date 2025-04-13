

- Contacts
- CNContactStore
-  defaultContainerIdentifier() 

Instance Method

# defaultContainerIdentifier()

Returns the identifier of the default container.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+visionOS 1.0+watchOS 2.0+

``` source
func defaultContainerIdentifier() -> String
```

## Return Value

The identifier of the default container.

## Discussion

This identifier can be used to fetch a default container. A default container is where the user wants new contacts to be added implicitly.

## See Also

### Fetching groups and containers

func groups(matching: NSPredicate?) throws -> [CNGroup]

Fetches all groups matching the specified predicate.

func containers(matching: NSPredicate?) throws -> [CNContainer]

Fetches all containers matching the specified predicate.

