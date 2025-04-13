

- AppKit
- NSRuleEditor
-  setCriteria(\_:andDisplayValues:forRowAt:) 

Instance Method

# setCriteria(\_:andDisplayValues:forRowAt:)

Modifies the row at a given index to contain the given items and values.

macOS

``` source
@MainActor
func setCriteria(
    _ criteria: [Any],
    andDisplayValues values: [Any],
    forRowAt rowIndex: Int
)
```

## Parameters 

`criteria`  

The array of criteria for the row at `rowIndex`. Pass an empty array to force the receiver to query its delegate. This value must not be `nil`.

Important

Raises an `NSInvalidArgumentException` if `criteria` is `nil`.

`values`  

The array of values for the row at `rowIndex`. Pass an empty array to force the receiver to query its delegate. This value must not be `nil`.

Important

Raises an `NSInvalidArgumentException` if `values` is `nil`.

`rowIndex`  

The index of a row in the receiver.

Important

Raises an `NSRangeException` if `rowIndex` is equal to or larger than the number of rows, or less than `0`.

## Discussion

It is your responsibility to ensure that each item in the array is a child of the previous item, and that the first item is a root item for the row type. If the last item has child items, then the items array will be extended by querying the delegate for child items until a childless item is reached. If `values` contains fewer objects than the (possibly extended) criteria array, then the delegate is queried to construct the remaining display values. If you want the delegate to be queried for all the criteria or all the display values, pass empty arrays; do not pass `nil`.

## See Also

### Providing Data

func reloadCriteria()

Instructs the receiver to refetch criteria from its delegate.

func criteria(forRow: Int) -> [Any]

Returns the currently chosen items for a given row.

func displayValues(forRow: Int) -> [Any]

Returns the chosen values for a given row.

