

- SwiftUI
- FetchRequest
-  init(sortDescriptors:predicate:animation:) 

Initializer

# init(sortDescriptors:predicate:animation:)

Creates a fetch request based on a predicate and reference type sort parameters.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
@MainActor @preconcurrency
init(
    sortDescriptors: [NSSortDescriptor],
    predicate: NSPredicate? = nil,
    animation: Animation? = nil
)
```

Available when `Result` inherits `NSManagedObject`.

Show all declarations

## Parameters 

`sortDescriptors`  

An array of sort descriptors that define the sort order of the fetched results.

`predicate`  

An NSPredicate instance that defines logical conditions used to filter the fetched results.

`animation`  

The animation to use for user interface changes that result from changes to the fetched results.

## Discussion

The request gets the entity type from the `Result` instance by calling that managed object’s entity() type method. If you need to specify the entity type explicitly, use the init(entity:sortDescriptors:predicate:animation:) initializer instead. If you need more control over the fetch request configuration, use init(fetchRequest:animation:).

## See Also

### Creating a fetch request

init(entity: NSEntityDescription, sortDescriptors: [NSSortDescriptor], predicate: NSPredicate?, animation: Animation?)

Creates a fetch request for a specified entity description, based on a predicate and sort parameters.

