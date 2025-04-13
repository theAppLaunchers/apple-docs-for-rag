

- SwiftData
- Query
-  modelContext 

Instance Property

# modelContext

Current model context `Query` interacts with.

SwiftDataSwiftUIiOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

``` source
@MainActor @preconcurrency
var modelContext: ModelContext { get }
```

## Discussion

Access this value from `Query` property wrapper’s stored property:

```
struct RecipeList: View {
    @Query var recipes: [Recipe]
    var body: some View {
        ChangesIndicator(
            hasChanges: _recipes.modelContext.hasChanges)
    }
}
```

Only access this property within of a view’s `body` property, otherwise its value may be invalid.

## See Also

### Getting query configuration

var fetchError: (any Error)?

An error encountered during the most recent attempt to fetch data.

