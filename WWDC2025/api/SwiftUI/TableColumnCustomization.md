*   [SwiftUI](/documentation/swiftui)
*   TableColumnCustomization

Structure

# TableColumnCustomization

A representation of the state of the columns in a table.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+visionOS 1.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
struct TableColumnCustomization<RowValue> where RowValue : [`Identifiable`](/documentation/Swift/Identifiable)
```
```
```
```
```
```
```
```

## [Overview](/documentation/SwiftUI/TableColumnCustomization#overview)

`TableColumnCustomization` can be created and provided to a table to enable column reordering and column visibility. The state can be queried and updated programmatically, as well as bound to persistent app or scene storage.

```swift
```swift
```swift
```swift
```swift
```swift
struct BugReportTable: View {
```
```
    @ObservedObject var dataModel: DataModel
    @Binding var selectedBugReports: Set<BugReport.ID>
    @SceneStorage("BugReportTableConfig")
    private var columnCustomization: TableColumnCustomization<BugReport>
    var body: some View {
        Table(dataModel.bugReports, selection: $selectedBugReports,
            sortOrder: $dataModel.sortOrder,
            columnCustomization: $columnCustomization
        ) {
            TableColumn("Title", value: \.title)
                .customizationID("title")
            TableColumn("ID", value: \.id) {
                Link("\($0.id)", destination: $0.url)
            }
            .customizationID("id")
            TableColumn("Number of Reports", value: \.duplicateCount) {
                Text($0.duplicateCount, format: .number)
            }
            .customizationID("duplicates")
        }
    }
}
```
```
```
```

The above example creates a table with three columns. On macOS, these columns can be reordered or hidden and shown by the user of the app. Their configuration will be saved and restored with the window on relaunches of the app, using the “BugReportTableConfig” scene storage identifier.

The state of a specific column is stored relative to its customization identifier, using using the value from the [`customizationID(_:)`](/documentation/swiftui/tablecolumncontent/customizationid\(_:\)) modifier. When column customization is encoded and decoded, it relies on stable identifiers to restore the associate the saved state with a specific column. If a table column does not have a customization identifier, it will not be customizable.

These identifiers can also be used to programmatically change column customizations, such as programmatically hiding a column:

```

```
columnCustomization[visibility: "duplicates"] = .hidden
```

```

With a binding to the overall customization, a binding to the visibility of a column can be accessed using the same subscript syntax:

```swift
```swift
```swift
```swift
```swift
```swift
struct BugReportTable: View {
```
```
    @SceneStorage("BugReportTableConfig")
    private var columnCustomization: TableColumnCustomization<BugReport>
    var body: some View {
        ...
        MyVisibilityView($columnCustomization[visibility: "duplicates"])
    }
}
```swift
```swift
struct MyVisibilityView: View {
```
```
    @Binding var visibility: Visibility
    ...
}
```
```
```
```

## [Topics](/documentation/SwiftUI/TableColumnCustomization#topics)

### [Creating a table column customization](/documentation/SwiftUI/TableColumnCustomization#Creating-a-table-column-customization)

[`init()`](/documentation/swiftui/tablecolumncustomization/init\(\))

Creates an empty table column customization.

### [Managing the customization](/documentation/SwiftUI/TableColumnCustomization#Managing-the-customization)

```swift
```swift
```swift
```swift
func resetOrder()
```
```

Resets the column order back to the default, preserving the customized visibility and size.
```

[`subscript(visibility _: String) -> Visibility`](/documentation/swiftui/tablecolumncustomization/subscript\(visibility:\))

The visibility of the column identified by its identifier.
```

## [Relationships](/documentation/SwiftUI/TableColumnCustomization#relationships)

### [Conforms To](/documentation/SwiftUI/TableColumnCustomization#conforms-to)

*   [`Decodable`](/documentation/Swift/Decodable)
*   [`Encodable`](/documentation/Swift/Encodable)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Sendable`](/documentation/Swift/Sendable)
*   [`SendableMetatype`](/documentation/Swift/SendableMetatype)

## [See Also](/documentation/SwiftUI/TableColumnCustomization#see-also)

### [Customizing columns](/documentation/SwiftUI/TableColumnCustomization#Customizing-columns)

```swift
```swift
```swift
```swift
func tableColumnHeaders(Visibility) -> some View
```
```

Controls the visibility of a `Table`’s column header views.
```
```swift
```swift
```swift
struct TableColumnCustomizationBehavior
```
```

A set of customization behaviors of a column that a table can offer to a user.
```
```