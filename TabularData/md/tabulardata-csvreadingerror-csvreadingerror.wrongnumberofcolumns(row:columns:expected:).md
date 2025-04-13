

- TabularData
- CSVReadingError
-  CSVReadingError.wrongNumberOfColumns(row:columns:expected:) 

Case

# CSVReadingError.wrongNumberOfColumns(row:columns:expected:)

An error that indicates the CSV data contains a row with a mismatched number of columns.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
case wrongNumberOfColumns(
    row: Int,
    columns: Int,
    expected: Int
)
```

## Parameters 

`row`  

The index of the row that contains the mismatched number of columns.

`columns`  

The number of columns in the row.

`expected`  

The number of columns in the other rows.

## See Also

### Getting Error Information

var column: Int?

The index of the column that contains the error.

var row: Int

The index of the row that contains the error.

case badEncoding(row: Int, column: Int, cellContents: Data)

An error that indicates CSV data contains an invalid UTF-8 byte sequence.

case failedToParse(row: Int, column: Int, type: CSVType, cellContents: Data)

An error that indicates the CSV reader can’t parse data in the file.

case misplacedQuote(row: Int, column: Int)

An error that indicates the CSV data contains a misplaced quote.

case missingColumn(columnName: String)

An error that indicates the CSV is missing a required column.

case unsupportedEncoding(String)

An error that indicates the CSV reader doesn’t support an encoding.

