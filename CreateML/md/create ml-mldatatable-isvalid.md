

- Create ML
- MLDataTable
-  isValid 

Instance Property

# isValid

A Boolean value that indicates whether the data table is valid.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 10.14+tvOS 16.0+visionOS 1.0+

``` source
var isValid: Bool { get }
```

## Discussion

Check isValid after you create or mutate a data table to ensure the data table is still valid. If it’s false, the data table encountered an error and you can’t use it for training or subsequent operations. The following are some of the actions that can invalidate a data table:

- Adding a column with the name of a column that already exists in the data table

- Adding an invalid column

- Appending another data table with different column names

- Appending another data table with different column types (for a given column name)

## See Also

### Handling data table errors

var error: (any Error)?

The underlying error present when the data table is invalid.

