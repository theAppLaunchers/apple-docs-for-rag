

- Foundation
- Locale
- Locale.Collation
-  searchRules 

Type Property

# searchRules

A collation used for string search.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
static let searchRules: Locale.Collation
```

## Discussion

Use this collation only for determining whether to consider two strings as equivalent. Using this collation may modify the string for search purposes. For example, this colloation supresses the contractions in Thai and Lao.

Don’t use this collation to determine the relative order of two strings.

## See Also

### Using special-purpose collations

static let standard: Locale.Collation

A collation that provides the default ordering for each language.

