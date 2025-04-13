

- SwiftUI
-  TableColumnContent 

Protocol

# TableColumnContent

A type used to represent columns within a table.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 12.0+visionOS 1.0+

``` source
@MainActor @preconcurrency
protocol TableColumnContent
```

## Overview

This type provides the body content of the column, as well as the types of the column’s row values and the comparator used to sort rows.

You can factor column content out into separate types or properties, or by creating a custom type conforming to `TableColumnContent`.

```
var body: some View {
    Table(people, selection: $selectedPeople, sortOrder: $sortOrder) {
        nameColumns

        TableColumn("Location", value: \.location) {
            LocationView($0.location)
        }
    }
}

@TableColumnBuilder>
private var nameColumns: some TableColumnContent
> {
    TableColumn("First Name", value: \.firstName) {
        PrimaryColumnView(person: $0)
    }
    TableColumn("Last Name", value: \.lastName)
    TableColumn("Nickname", value: \.nickname)
}
```

The above example factors three table columns into a separate computed property that has an opaque type. The property’s primary associated type `TableRowValue` is a `Person` and its associated type `TableColumnSortComparator` is a key comparator for the `Person` type.

A type conforming to this protocol inherits `@preconcurrency @MainActor` isolation from the protocol if the conformance is included in the type’s base declaration:

```
struct MyCustomType: Transition {
    // `@preconcurrency @MainActor` isolation by default
}
```

Isolation to the main actor is the default, but it’s not required. Declare the conformance in an extension to opt out of main actor isolation:

```
extension MyCustomType: Transition {
    // `nonisolated` by default
}
```

## Topics

### Getting the column body

var tableColumnBody: Self.TableColumnBody

The composition of content that comprise the table column content.

**Required**

associatedtype TableColumnBody : TableColumnContent

The type of content representing the body of this table column content.

**Required**

### Defining the row value

associatedtype TableRowValue : Identifiable = Self.TableColumnBody.TableRowValue

The type of value of rows presented by this column content.

**Required**

### Defining the comparator

associatedtype TableColumnSortComparator : SortComparator = Self.TableColumnBody.TableColumnSortComparator

The type of sort comparator associated with this table column content.

**Required**

### Configuring the content

func alignment(TableColumnAlignment) -> some TableColumnContent&lt;Self.TableRowValue, Self.TableColumnSortComparator> 

Sets the alignment of the column, applying to both its column header label and the row view content for that column.

func customizationID(String) -> some TableColumnContent&lt;Self.TableRowValue, Self.TableColumnSortComparator> 

Sets the identifier to be associated with a column when persisting its state with `TableColumnCustomization`.

func defaultVisibility(Visibility) -> some TableColumnContent&lt;Self.TableRowValue, Self.TableColumnSortComparator> 

Sets the default visibility of a table column.

func disabledCustomizationBehavior(TableColumnCustomizationBehavior) -> some TableColumnContent&lt;Self.TableRowValue, Self.TableColumnSortComparator> 

Sets the disabled customization behavior for a table column.

## Relationships

### Conforming Types

- Group

  Conforms when `Content` conforms to `TableColumnContent`.

- TableColumn
- TableColumnForEach
- TupleTableColumnContent

## See Also

### Creating columns

struct TableColumn

A column that displays a view for each row in a table.

struct TableColumnAlignment

Describes the alignment of the content of a table column.

struct TableColumnBuilder

A result builder that creates table column content from closures.

struct TableColumnForEach

A structure that computes columns on demand from an underlying collection of identified data.

