

- Core Spotlight
- CSUserQueryContext
-  enableRankedResults 

Instance Property

# enableRankedResults

A Boolean value that indicates whether the query sorts results by their relevance.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+visionOS 1.0+

``` source
var enableRankedResults: Bool { get set }
```

## Discussion

The default value of this property is `true`. Setting the property to `false` causes Spotlight to return results as it finds them instead of ordering them by their relevance or saliency to the search term.

## See Also

### Configuring the ranked results behavior

var maxRankedResultCount: Int

The maximum number of ranked results to return during the query.

