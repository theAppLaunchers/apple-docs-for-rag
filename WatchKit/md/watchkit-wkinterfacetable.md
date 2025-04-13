

- WatchKit
-  WKInterfaceTable 

Class

# WKInterfaceTable

An object that creates and manages the contents of a single-column table interface.

watchOS 2.0+

``` source
class WKInterfaceTable
```

## Mentioned in 

Navigating Between Scenes

## Overview

You use a table object to set the number and type of rows and to configure the data objects for those rows. Take the following steps to configure a table object and fill it with data:

1.  Define one or more row controller types in your storyboard.

2.  Define a custom data class to manage the contents of each row type.

3.  Tell the table object how many rows (and of what type) to display at runtime.

4.  Use instances of your custom data class to configure each row’s contents.

Don’t subclass or create instances of this class yourself. Instead, define outlets in your interface controller class and connect them to the corresponding objects in your storyboard file. For example, to refer to a table object in your interface, define a property with the following syntax in your interface controller class:

- Swift
- Objective-C

```
@IBOutlet weak var myTable: WKInterfaceTable!
```

```
@property (weak, nonatomic) IBOutlet WKInterfaceTable* myTable;
```

During the initialization of your interface controller, WatchKit creates a new instance of this class and assigns it to your outlet. At that point, you can use the object in your outlet to make changes to the table.

### Define Your Table’s Rows

After adding a table object to your storyboard, configure the row controller that comes with the table. A row controller defines the appearance of a specific type of row. A table comes with one row type initially and you can add more later. Each row controller in your table requires some minimal configuration to be usable at runtime.

- Each row controller must have a name, which you set using the Identifier property in the Attributes inspector. You use this name to create rows of that type later.

- Each row controller must have an associated class, which you set in the Identity inspector. At runtime, the table creates instances of your row controller classes for each row in the table.

To configure the contents of a row controller, drag elements from the library and drop them onto the row’s group. For most rows, use a group object as the top-level object. You can also nest group objects to create vertical and horizontal arrangements for your interface objects. To that group, add the objects needed to display the row’s contents.

Each row controller needs a class to manage the contents of the row at runtime. The class acts as a proxy for the row in your code and stores the outlets you need to configure the contents of the row.

- Swift
- Objective-C

```
class MyRowController: NSObject {
    @IBOutlet weak var itemLabel: WKInterfaceLabel!
    @IBOutlet weak var itemImage: WKInterfaceImage!
}
```

```
@interface MyRowController : NSObject
@property (weak, nonatomic) IBOutlet WKInterfaceLabel* itemLabel;
@property (weak, nonatomic) IBOutlet WKInterfaceImage* itemImage;
@end
```

### Set the Number of Rows at Runtime

To fill a table interface object with data, use the setRowTypes(_:) or setNumberOfRows(_:withRowType:) method. These methods specify the type (and number) of rows to add to the table. If all rows are of the same type, use the setNumberOfRows(_:withRowType:) method. If you use more than one row controller in your table, use the setRowTypes(_:) method. The row type string corresponds to the name you entered into the Identifier property for that row controller in your storyboard.

When you add rows to a table, WatchKit creates the rows in your Watch app and instantiates the classes corresponding to those rows in your WatchKit extension. The table object stores the newly instantiated classes internally and makes them available to you through the rowController(at:) method. Use that method to retrieve each row controller object and configure the contents of the row.

- Swift
- Objective-C

```
func loadTodoItems() {
    // Fetch the to-do items
    let items = myFetchToDoList()

    // Configure the table object and get the row controllers.
    myTable.setNumberOfRows(items.count, withRowType: "MainRowType")

    // Iterate over the rows and set the label and image for each one.
    for (index, item) in items.enumerated() {
        let row = myTable.rowController(at: index) as! MyRowController
        row.itemImage.setImage(item.image)
        row.itemLabel.setText(item.title)
    }
}
```

```
- (void)loadTodoItems {
    // Fetch the to-do items
    NSArray* items = [self fetchTodoList];

    // Configure the table object and get the row controllers.
    NSInteger rowCount = items.count;
    [self.myTable setNumberOfRows:rowCount withRowType:@"MainRowType"];

    // Iterate over the rows and set the label and image for each one.
    for (NSInteger i = 0; i 

In this example, the table gets the data for the rows, and then calls the table’s setNumberOfRows(_:withRowType:) method to create the rows. It then iterates over the newly created row controller objects, configuring each one’s label with the text for the to-do item.

When you want to update the contents of a table, call setRowTypes(_:) or setNumberOfRows(_:withRowType:) again with the new row type information. Calling these methods again forces the table to discard the old rows and create new ones. To insert new rows without removing the old ones, use the insertRows(at:withRowType:) method.

### Respond to Taps in Table Rows

In your storyboard, create a segue between a row controller and a destination interface controller. When the user taps on a row of that type, the system automatically pushes the destination interface controller onto the screen. To pass data to the destination controller, override your current interface controller’s contextForSegue(withIdentifier:in:rowIndex:) method, and return context data based on the selected row.

Alternatively, you can explicitly respond to taps in a table row by implementing your interface controller’s table(_:didSelectRowAt:) method. Use that method to present a different interface controller or to perform any other relevant tasks.

Note

Row controllers that include controls such as switches, sliders, and buttons must use action methods to respond to interactions with those controls. The system doesn’t deliver taps in controls to your interface controller’s table(_:didSelectRowAt:) method.

### Support Item Pagination

Item Pagination lets users easily navigate through lists of items. When the user selects an item from the table, the app displays a detailed view for the item. The user can then scroll up and down to navigate between other sibling items from that table. For example if the user selects a stock symbol in the Stocks app, it loads the details for that stock. They can then scroll vertically to navigate to other stocks.

Item Pagination is disabled by default. To enable it, perform the following steps:

1.  In the storyboard, enable the table’s Item Pagination option in the Attributes inspector.

2.  In the storyboard, define segues for all of the table’s row controllers. Your table must use segues to drive its navigation.

3.  If you programmatically navigate through a table’s items (for example, when launching from a complication to a specific interface controller), be sure to use the table’s performSegue(forRow:) method, instead of the interface controller’s pushController(withName:context:) method. The performSegue(forRow:) method lets watchOS know which table and which row initiated the segue. The system needs this information to provide the correct sibling items as the user scrolls.

### Configure the Table’s Attributes

Xcode lets you configure information about your table interface object in your storyboard file. The following table lists the attributes you can configure in your storyboard and their meaning.

| Attribute | Description |
|----|----|
| Rows | The number of row controllers supported by the table. Change the value to add or remove new row controller objects to the storyboard file. |
| Spacing | The amount of spacing (in points) between rows. |
| Background | The background image to display behind the table’s items. Don’t set an image if you want the background color or image of the underlying interface controller to be visible. |
| Color | The background color for the table. Set the color to clear if you want the background color or image of the underlying interface controller to be visible. |
| Item Pagination | A checkbox that enables Item Pagination. For more information on Item Pagination, see Support Item Pagination. |

For each row controller in your table, The following table lists the attributes you can configure and their meaning.

| Attribute | Description |
|----|----|
| Identifier | The name used to identify the row controller’s type to the setRowTypes(_:) or setNumberOfRows(_:withRowType:) method. |
| Selectable | A checkbox indicating whether the table responds to taps within the row. When disabled, tapping the row doesn’t highlight the row or report the action to the table. |

## Topics

### Specifying the Row Types

func setRowTypes([String])

Creates the row controllers to use when populating the table with data.

func setNumberOfRows(Int, withRowType: String)

Creates the specified number of row controllers (of the same type) to use in populating the table with data.

### Getting the Row Controllers

var numberOfRows: Int

The number of row controllers available for you to retrieve.

func rowController(at: Int) -> Any?

Returns the row controller for the row at the specified index in the table.

### Inserting and Removing Rows

func insertRows(at: IndexSet, withRowType: String)

Inserts rows into the table at the specified indexes.

func removeRows(at: IndexSet)

Removes the specified rows from the table.

### Scrolling

func scrollToRow(at: Int)

Scrolls the row at the specified index into view.

var curvesAtBottom: Bool

A Boolean value that determines whether the rows shrink to match the curved corners at the bottom of the screen.

var curvesAtTop: Bool

A Boolean value that determines whether the rows shrink to match the curved corners at the top of the screen.

### Performing segues

func performSegue(forRow: Int)

Performs the segue for the specified row.

## Relationships

### Inherits From

- WKInterfaceObject

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSObjectProtocol

## See Also

### Containers

class WKInterfaceGroup

A container for one or more interface objects.

class WKInterfaceSeparator

An interface object that displays a visual separator within a group.

class WKInterfacePicker

An interface element that presents a scrolling list of items for the user to choose from.

