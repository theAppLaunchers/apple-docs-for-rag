

- SwiftData
- FetchDescriptor
-  fetchLimit 

Instance Property

# fetchLimit

The maximum number of models the fetch can return.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+Swift 5.9+

``` source
var fetchLimit: Int?
```

## Discussion

Important

Use `nil` to tell the fetch to return all models of the associated type, not `0`.

The default value is `nil`.

## See Also

### Constraining the fetch

var predicate: Predicate&lt;T>?

The logical condition that determines whether the fetch includes a specific model in its results.

var sortBy: [SortDescriptor&lt;T>]

The sort descriptors that tell the fetch how to order its results.

var fetchOffset: Int?

The offset of the first matching model to fetch.

var includePendingChanges: Bool

A Boolean value that indicates whether, when the fetch runs, it matches against currently unsaved changes in the model context.

