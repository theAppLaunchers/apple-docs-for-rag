Framework

# TabularData

Import, organize, and prepare a table of data to train a machine learning model.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

## [Topics](/documentation/TabularData#topics)

### [Data Tables](/documentation/TabularData#Data-Tables)

```swift
```swift
```swift
```swift
struct DataFrame
```
```

A collection that arranges data in rows and columns.
```
```swift
```swift
```swift
protocol DataFrameProtocol
```
```

A type that represents a data frame.
```
```

### [Typed Columns](/documentation/TabularData#Typed-Columns)

```swift
```swift
```swift
```swift
struct Column
```
```

A column in a data frame.
```
```swift
```swift
```swift
struct ColumnSlice
```
```

A collection that represents a selection of contiguous elements from a typed column.
```
```swift
```swift
```swift
struct FilledColumn
```
```

A view on a column that replaces missing elements with a default value.
```
```swift
```swift
```swift
struct DiscontiguousColumnSlice
```
```

A collection that represents a selection, potentially with gaps, of elements from a typed column.
```
```swift
```swift
```swift
protocol ColumnProtocol
```
```

A type that represents a column.
```
```swift
```swift
```swift
protocol OptionalColumnProtocol
```
```

A type that represents a column that has missing values.
```
```

### [Type-Erased Columns](/documentation/TabularData#Type-Erased-Columns)

```swift
```swift
```swift
```swift
struct AnyColumn
```
```

A type-erased column.
```
```swift
```swift
```swift
struct AnyColumnSlice
```
```

A type-erased column slice.
```
```swift
```swift
```swift
protocol AnyColumnProtocol
```
```

A type that represents a type-erased column.
```
```swift
```swift
```swift
protocol AnyColumnPrototype
```
```

A prototype that creates type-erased columns.
```
```

### [Statistical Summaries](/documentation/TabularData#Statistical-Summaries)

```swift
```swift
```swift
```swift
struct NumericSummary
```
```

A summary of a numerical column.
```
```swift
```swift
```swift
struct CategoricalSummary
```
```

A categorical summary of a collection’s elements.
```
```swift
```swift
```swift
struct AnyCategoricalSummary
```
```

A type-erased categorical summary.
```
```

### [Errors](/documentation/TabularData#Errors)

```swift
```swift
```swift
```swift
enum JSONReadingError
```
```

A JSON reading error.
```
```swift
```swift
```swift
enum CSVReadingError
```
```

A CSV reading error.
```
```swift
```swift
```swift
enum CSVWritingError
```
```

A CSV writing error.
```
```swift
```swift
```swift
struct ColumnDecodingError
```
```

A column decoding error.
```
```swift
```swift
```swift
struct ColumnEncodingError
```
```

A column encoding error.
```
```swift
```swift
```swift
enum SFrameReadingError
```
```

An error when reading a Turi Create scalable data frame.
```
```

### [Supporting Types](/documentation/TabularData#Supporting-Types)

```swift
```swift
```swift
```swift
enum Order
```
```

A type that represents a sort ordering.
```
```swift
```swift
```swift
struct ColumnID
```
```

A column identifier that stores a column’s name and the type of its elements.
```
```swift
```swift
```swift
struct FormattingOptions
```
```

A set of parameters that indicate how to present the contents of data frame or column types to a printable string.
```
```

### [Structures](/documentation/TabularData#Structures)

```swift
```swift
```swift
```swift
struct JSONWritingOptions
```
```

A set of JSON file-reading options.
```
```