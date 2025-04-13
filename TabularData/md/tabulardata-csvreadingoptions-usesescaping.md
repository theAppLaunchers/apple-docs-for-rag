

- TabularData
- CSVReadingOptions
-  usesEscaping 

Instance Property

# usesEscaping

A Boolean value that indicates whether to enable escaping.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
var usesEscaping: Bool
```

## Discussion

When `true`, you can escape special characters, such as the field delimiter, by prefixing them with the escape character, which is the backslash (`\`) by default. Defaults to `false`.

