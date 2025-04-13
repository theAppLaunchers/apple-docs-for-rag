

- SwiftUI
-  TableColumnBuilder 

Structure

# TableColumnBuilder

A result builder that creates table column content from closures.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 12.0+visionOS 1.0+

``` source
@resultBuilder
struct TableColumnBuilder where RowValue : Identifiable, Sort : SortComparator
```

## Overview

The `buildBlock` methods in this type create TableColumnContent instances based on the number and types of sources provided as parameters.

Don’t use this type directly; instead, SwiftUI annotates the `columns` parameter of the various Table initializers with the `@TableColumnBuilder` annotation, implicitly calling this builder for you.

## Topics

### Building a column

static buildBlock(_:)

Creates a single, unsortable column result.

static buildBlock(_:_:)

Creates an unsortable column result from two sources.

static buildBlock(_:_:_:)

Creates an unsortable column result from three sources.

static buildBlock(_:_:_:_:)

Creates an unsortable column result from four sources.

static buildBlock(_:_:_:_:_:)

Creates an unsortable column result from five sources.

static buildBlock(_:_:_:_:_:_:)

Creates an unsortable column result from six sources.

static buildBlock(_:_:_:_:_:_:_:)

Creates an unsortable column result from seven sources.

static buildBlock(_:_:_:_:_:_:_:_:)

Creates an unsortable column result from eight sources.

static buildBlock(_:_:_:_:_:_:_:_:_:)

Creates an unsortable column result from nine sources.

static buildBlock(_:_:_:_:_:_:_:_:_:_:)

Creates an unsortable column result from ten sources.

static buildExpression(_:)

Creates a generic, unsortable single column expression.

### Supporting types

struct TupleTableColumnContent

A type of table column content that creates table columns created from a Swift tuple of table columns.

### Type Methods

static buildEither(first:)

Creates a column result for the first of two column content alternatives.

static buildEither(second:)

Creates a row result for the second of two row content alternatives.

static buildIf(_:)

static buildLimitedAvailability(_:)

## See Also

### Creating columns

struct TableColumn

A column that displays a view for each row in a table.

protocol TableColumnContent

A type used to represent columns within a table.

struct TableColumnAlignment

Describes the alignment of the content of a table column.

struct TableColumnForEach

A structure that computes columns on demand from an underlying collection of identified data.

