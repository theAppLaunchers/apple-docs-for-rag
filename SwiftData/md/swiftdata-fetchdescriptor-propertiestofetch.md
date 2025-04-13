

- SwiftData
- FetchDescriptor
-  propertiesToFetch 

Instance Property

# propertiesToFetch

The specific subset of attributes to fetch if you don’t require them all.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+Swift 5.9+

``` source
var propertiesToFetch: [PartialKeyPath]
```

## Discussion

If you know ahead of time that you’re going to process (or display) a subset of a model’s attributes, use this property to provide the key paths of those attributes. When the fetch runs, it’ll return values for only the specified key paths, which may result in faster and more efficient fetches. However, if you subsequently access a nonfetched attribute, you’ll incur the additional overhead of fetching the corresponding value from the persistent storage.

Note

An empty array causes the fetch to include all attributes, not none.

The default value is an empty array.

## See Also

### Specifying the fetched attributes

var relationshipKeyPathsForPrefetching: [PartialKeyPath&lt;T>]

The key paths that identify any related models to include as part of the fetch.

