

- Create ML Components
- ConcatenationError
-  ConcatenationError.mismatchedShapes 

Case

# ConcatenationError.mismatchedShapes

Shaped arrays across columns have mismatched shapes and can’t be concatenated.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 11.0+

``` source
case mismatchedShapes
```

## See Also

### Analyzing the error

case nonUniformShapes(columnName: String)

A column contains arrays or shaped arrays with non-uniform shapes.

var errorDescription: String?

A localized message describing what error occurred.

