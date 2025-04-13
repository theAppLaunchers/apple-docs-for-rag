

- Foundation
- NSComparisonPredicate
- NSComparisonPredicate.Options
-  caseInsensitive 

Type Property

# caseInsensitive

A case-insensitive predicate.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
static var caseInsensitive: NSComparisonPredicate.Options { get }
```

## Discussion

You represent this option in a predicate format string using a `[c]` following a string operation (for example, `"NeXT" like[c] "next"`).

## See Also

### Constants

static var diacriticInsensitive: NSComparisonPredicate.Options

A diacritic-insensitive predicate.

static var normalized: NSComparisonPredicate.Options

A predicate that indicates you’ve preprocessed the strings to compare.

static var diacriticInsensitive: NSComparisonPredicate.Options

A diacritic-insensitive predicate.

static var normalized: NSComparisonPredicate.Options

A predicate that indicates you’ve preprocessed the strings to compare.

