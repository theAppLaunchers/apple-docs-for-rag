

- Create ML
- MLDataTable
-  unpack(columnNamed:valueTypes:indexSubset:keySubset:) 

Instance Method

# unpack(columnNamed:valueTypes:indexSubset:keySubset:)

Creates a new data table with additional columns that contain the unpacked collections in the given column.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 11.0+tvOS 16.0+visionOS 1.0+

``` source
func unpack(
    columnNamed: String,
    valueTypes: [MLDataValue.ValueType]? = nil,
    indexSubset: [Int]? = nil,
    keySubset: [String]? = nil
) -> MLDataTable
```

## Return Value

A new data table.

## Discussion

This function performs the inverse of pack(columnsNamed:to:type:filling:).

- columnNamed: The name of the column to unpack. The underlying type of the column must be either MLDataValue.SequenceType or MLDataValue.DictionaryType.

- valueTypes: An array of the underlying types for the new, unpacked columns. If `nil`, the method infers the underlying types in the sequence or dictionary.

  Note

  If not `nil`, the method unpacks `valueTypes.count` columns.

- indexSubset: The subset of indicies to unpack from a specified sequence-typed column. If `nil`, the method unpacks all indicies.

- keySubset: The subset of keys to unpack from a specified dictionary-typed column. If `nil`, the method unpacks all keys.

