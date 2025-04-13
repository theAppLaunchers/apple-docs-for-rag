

- SwiftData
- FetchDescriptor
-  predicate 

Instance Property

# predicate

The logical condition that determines whether the fetch includes a specific model in its results.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+Swift 5.9+

``` source
var predicate: Predicate?
```

## Discussion

Use this property to replace or remove the fetch descriptor’s predicate. If the value is `nil`, any fetch using the descriptor will return all models of the associated type.

The default value is the predicate you specify when calling init(predicate:sortBy:).

## See Also

### Constraining the fetch

var sortBy: [SortDescriptor&lt;T>]

The sort descriptors that tell the fetch how to order its results.

var fetchLimit: Int?

The maximum number of models the fetch can return.

var fetchOffset: Int?

The offset of the first matching model to fetch.

var includePendingChanges: Bool

A Boolean value that indicates whether, when the fetch runs, it matches against currently unsaved changes in the model context.

