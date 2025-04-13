

- WatchKit
- WKInterfaceTable
-  insertRows(at:withRowType:) 

Instance Method

# insertRows(at:withRowType:)

Inserts rows into the table at the specified indexes.

watchOS 2.0+

``` source
func insertRows(
    at rows: IndexSet,
    withRowType rowType: String
)
```

## Parameters 

`rows`  

An index set containing the locations for the new rows. Each new row controller object is inserted into the array of row controllers in turn and at the specified index after earlier insertions have been made.

`rowType`  

The type of the row controllers to insert. This string corresponds to the value in the Identifier attribute of a row controller definition in your storyboard file.

## Discussion

This method inserts the new row controllers into the existing array of row controllers using the semantics defined by the insert(_:at:) method of NSMutableArray.

## See Also

### Inserting and Removing Rows

func removeRows(at: IndexSet)

Removes the specified rows from the table.

