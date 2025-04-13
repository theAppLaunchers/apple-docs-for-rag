

- UIKit
-  UITableViewDataSource 

Protocol

# UITableViewDataSource

The methods that an object adopts to manage data and provide cells for a table view.

iOSiPadOSMac CatalysttvOSvisionOS

``` source
@MainActor
protocol UITableViewDataSource : NSObjectProtocol
```

## Mentioned in 

Filling a table with data

## Overview

Table views manage only the presentation of their data; they don’t manage the data itself. To manage the data, you provide the table with a data source object — an object that implements the UITableViewDataSource protocol. A data source object responds to data-related requests from the table. It also manages the table’s data directly, or coordinates with other parts of your app to manage that data. Other responsibilities of the data source object include:

- Reporting the number of sections and rows in the table.

- Providing cells for each row of the table.

- Providing titles for section headers and footers.

- Configuring the table’s index, if any.

- Responding to user- or table-initiated updates that require changes to the underlying data.

Only two methods of this protocol are required, and they’re shown in the following example code.

```
// Return the number of rows for the table.     
override func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
   return 0
}

// Provide a cell object for each row.
override func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
   // Fetch a cell of the appropriate type.
   let cell = tableView.dequeueReusableCell(withIdentifier: "cellTypeIdentifier", for: indexPath)

   // Configure the cell’s contents.
   cell.textLabel!.text = "Cell text"

   return cell
}
```

Use other methods of this protocol to enable specific features for your table. For example, you must implement the tableView(_:commit:forRowAt:) method to enable the swipe-to-delete feature for rows.

For information about how to create and configure your table’s cells using your data source object, see Filling a table with data.

### Specify the location of rows and sections

Table views communicate the location of cells to you using the row and section properties of NSIndexPath objects. Row and section indexes are zero based, so the first section is at index `0`, the second at index `1`, and so on. Similarly, the first row of each section is at index `0`, which means you need both the section and row values to identify a row uniquely. If your table has no sections, you need only the row value.

## Topics

### Providing the number of rows and sections

func tableView(UITableView, numberOfRowsInSection: Int) -> Int

Tells the data source to return the number of rows in a given section of a table view.

**Required**

func numberOfSections(in: UITableView) -> Int

Asks the data source to return the number of sections in the table view.

### Providing cells, headers, and footers

func tableView(UITableView, cellForRowAt: IndexPath) -> UITableViewCell

Asks the data source for a cell to insert in a particular location of the table view.

**Required**

func tableView(UITableView, titleForHeaderInSection: Int) -> String?

Asks the data source for the title of the header of the specified section of the table view.

func tableView(UITableView, titleForFooterInSection: Int) -> String?

Asks the data source for the title of the footer of the specified section of the table view.

### Inserting or deleting table rows

func tableView(UITableView, commit: UITableViewCell.EditingStyle, forRowAt: IndexPath)

Asks the data source to commit the insertion or deletion of a specified row.

func tableView(UITableView, canEditRowAt: IndexPath) -> Bool

Asks the data source to verify that the given row is editable.

### Reordering table rows

func tableView(UITableView, canMoveRowAt: IndexPath) -> Bool

Asks the data source whether a given row can move to another location in the table view.

func tableView(UITableView, moveRowAt: IndexPath, to: IndexPath)

Tells the data source to move a row at a specific location in the table view to another location.

### Configuring an index

func sectionIndexTitles(for: UITableView) -> [String]?

Asks the data source to return the titles for the sections of a table view.

func tableView(UITableView, sectionForSectionIndexTitle: String, at: Int) -> Int

Asks the data source to return the index of the section having the given title and section title index.

## Relationships

### Inherits From

- NSObjectProtocol

### Conforming Types

- UITableViewController
- UITableViewDiffableDataSource
- UITableViewDiffableDataSourceReference

## See Also

### Data

Filling a table with data

Create and configure cells for your table dynamically using a data source object, or provide them statically from your storyboard.

Asynchronously loading images into table and collection views

Store and fetch images asynchronously to make your app more responsive.

protocol UITableViewDataSourcePrefetching

A protocol that provides advance warning of the data requirements for a table view, allowing you to start potentially long-running data operations early.

class UITableViewDiffableDataSource

The object you use to manage data and provide cells for a table view.

struct NSDiffableDataSourceSnapshot

A representation of the state of the data in a view at a specific point in time.

class UILocalizedIndexedCollation

An object that organizes, sorts, and localizes the data for a table view that has a section index.

protocol UIDataSourceTranslating

An advanced interface for managing a data source object.

class UIRefreshControl

A standard control that can initiate the refreshing of a scroll view’s contents.

