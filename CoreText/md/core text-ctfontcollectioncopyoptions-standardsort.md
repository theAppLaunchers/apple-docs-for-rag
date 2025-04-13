

- Core Text
- CTFontCollectionCopyOptions
-  standardSort 

Type Property

# standardSort

Passing this option indicates that the return values should be sorted in standard UI order, suitable for display to the user. This is the same sorting behavior used by `NSFontPanel` and Font Book.

iOS 12.0+iPadOS 12.0+Mac Catalyst 13.1+macOS 10.7+tvOS 12.0+visionOS 1.0+watchOS 5.0+

``` source
static var standardSort: CTFontCollectionCopyOptions { get }
```

## See Also

### Constants

static var unique: CTFontCollectionCopyOptions

Passing this option indicates that duplicate values should be removed from the results.

