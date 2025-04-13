

- UIKit
- Views and controls
- Table views
-  Configuring the cells for your table 

Article

# Configuring the cells for your table

Specify the appearance and content of your table’s rows by defining one or more prototype cells in your storyboard.

## Overview

Cells provide the visual representation of your table’s rows. For most tables, you provide only one or two different types of cells. Design your cells to ensure that the most important information stands out. Do that using a careful choice of views and view configurations in your cells.

You specify the appearance of cells at design time in your storyboard file. Xcode provides one prototype cell for each table, and you can add more prototype cells as needed. A prototype cell acts a template for your cell’s appearance. It includes the views you want to display and their arrangement within the content area of the cell. At runtime, the table’s data source object creates actual cells from the prototypes and configures them with your app’s data.

For tips on how to design the appearance of your cells, see Human Interface Guidelines.

### Assign a reuse identifier to each cell

Reuse identifiers facilitate the creation and recycling of your table’s cells. A reuse identifier is a string that you assign to each prototype cell of your table. In your storyboard, select your prototype cell and assign a nonempty value to its identifier attribute. Each cell in a table view must have a unique reuse identifier.

When you need a cell object at runtime, call the table view’s dequeueReusableCell(withIdentifier:for:) method, passing the reuse identifier for the cell you want. The table view maintains an internal queue of already-created cells. If the queue contains a cell of the requested type, the table view returns that cell. If not, it creates a new cell using the prototype cell in your storyboard. Reusing cells improves performance by minimizing memory allocations during critical times, such as during scrolling.

```
var cell = tableView.dequeueReusableCell(withIdentifier: "myCellType", for: indexPath)
```

### Configure a cell with a built-in style

The simplest way to configure a cell is to use one of the built-in styles provided by UITableViewCell. You use these styles as is; you don’t need to provide a custom subclass to manage the cell. Each style incorporates one or two labels, with the style determining the positions of the labels within the cell’s content area. Most of the styles also incorporate an image at the leading edge of the cell’s content.

To configure a prototype cell with one of the standard styles, select the cell in your storyboard and set the cell’s Style property to a value other than custom.

In your tableView(_:cellForRowAt:) method, configure the content of your cell using the textLabel, detailTextLabel, and imageView properties of UITableViewCell. Those properties contain views, but the cell object only assigns a view if the style supports the corresponding content. For example, the Basic cell style doesn’t support a detail string, so the detailTextLabel property is `nil` for that style. The following example code shows how to configure a cell that uses the basic cell style.

```
override func tableView(_ tableView: UITableView, 
             cellForRowAt indexPath: IndexPath) -> UITableViewCell {
   // Reuse or create a cell. 
   let cell = tableView.dequeueReusableCell(withIdentifier: "basicStyle", for: indexPath)

   // For a standard cell, use the UITableViewCell properties.
   cell.textLabel!.text = "Title text"
   cell.imageView!.image = UIImage(named: "bunny")
   return cell
}
```

### Configure a cell with custom views

For appearances other than the standard styles, use the custom cell style. With a custom cell, you specify the views you want in the cell, their configurations, and their sizes and positions. Static views such as labels and images make the best content for cells. Avoid views that require user interactions such as controls. Don’t include scroll views, table views, collection views, or other complex container views in cells. You may include stack views in your cells, but minimize the number of items in your stack view to improve performance.

To configure a custom cell, drag views into the prototype cell for your table. The following illustration shows a cell with a custom layout and formatting for its views. You use constraints to position your views within the cell’s content area. When setting up constraints, use the “Constrain to margins” option to preserve the gap between the content areas of your cells.

For custom cells, you need to define a UITableViewCell subclass to access your cell’s views. Add outlets to your subclass and connect those outlets to the corresponding views in your prototype cell.

```
class FoodCell: UITableViewCell {
    @IBOutlet var name : UILabel?
    @IBOutlet var plantDescription : UILabel?
    @IBOutlet var picture : UIImageView?
}
```

In the tableView(_:cellForRowAt:) method of your data source, use your cell’s outlets to assign values to any views.

```
override func tableView(_ tableView: UITableView, 
             cellForRowAt indexPath: IndexPath) -> UITableViewCell {

   // Reuse or create a cell of the appropriate type.
   let cell = tableView.dequeueReusableCell(withIdentifier: "foodCellType", 
                         for: indexPath) as! FoodCell

   // Fetch the data for the row.
   let theFood = foods[indexPath.row]

   // Configure the cell’s contents with data from the fetched object.
   cell.name?.text = theFood.name
   cell.plantDescription?.text = theFood.description
   cell.picture?.image = theFood.picture

   return cell
}
```

### Change the height of rows

A table view tracks the height of rows separately from the cells that represent them. UITableView provides default sizes for rows, but you can override the default height by assigning a custom value to the table view’s rowHeight property. Always use this property when the height of all of your rows is the same. Doing so is more efficient than returning the height values from your delegate object.

If the row heights aren’t all the same, or can change dynamically, provide the heights using the tableView(_:heightForRowAt:) method of your delegate object. When you implement this method, you must provide values for every row in your table. The following example code shows how to return a custom height for the first row of each section and use the default height for all other rows.

```
override func tableView(_ tableView: UITableView, 
           heightForRowAt indexPath: IndexPath) -> CGFloat {
   // Make the first row larger to accommodate a custom cell.
  if indexPath.row == 0 {
      return 80
   }

   // Use the default size for all other rows.
   return UITableView.automaticDimension
}
```

The table view asks for the heights of visible rows only. As the user scrolls, the table view asks you to provide the height for each row as it appears, including when it moves offscreen and then back onscreen.

### Restore your cell’s original appearance before reuse

When a cell moves offscreen, the table view removes it from its view hierarchy and places it in an internally managed recycling queue. When you request a new cell using the table view’s dequeueReusableCell(withIdentifier:for:) method, the table view returns cells from the recycling queue first. If the queue is empty, the table view instantiates a new cell from your storyboard.

If you change the appearance of your custom cell’s views, implement the prepareForReuse() method of your cell subclass. In your implementation, return the appearance of your cell’s views to their original state. For example, if you change the alpha property of a view in your cell, return that property to its original value. You don’t need to clear label text, set images to `nil`, or do anything that would be corrected by your tableView(_:cellForRowAt:) method when configuring the cell for display.

### Add an accessory view to your cell

An accessory view is an optional, system-defined view that appears at the trailing edge of a cell. You use accessory views to communicate standard cell behaviors to users. For example, you add a detail button to let the user know that tapping the row displays more information about the row.

To configure an accessory view:

- In your storyboard, use the cell’s Accessory attribute to select the accessory view you want.

- In your code, change the value of the cell’s accessoryType property.

Users expect accessory views to have specific behaviors when tapped. For information about how to implement those behaviors, see UITableViewCell.AccessoryType.

## See Also

### Related Documentation

Estimating the height of a table’s scrolling area

Provide height estimates for your table view’s headers, footers, and rows to ensure that scrolling accurately reflects the size of your content.

### Cells, headers, and footers

Creating self-sizing table view cells

Create table view cells that support Dynamic Type and use system spacing constraints to adjust the spacing surrounding text labels.

Adding headers and footers to table sections

Differentiate groups of rows visually by adding header and footer views to your table view’s sections.

class UITableViewCell

The visual representation of a single row in a table view.

class UITableViewHeaderFooterView

A reusable view that you place at the top or bottom of a table section to display additional information for that section.

