

- Create ML
- MLDataTable
-  init(contentsOf:options:) 

Initializer

# init(contentsOf:options:)

Creates a data table from an imported JSON or CSV file.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 10.14+tvOS 16.0+visionOS 1.0+

``` source
init(
    contentsOf url: URL,
    options: MLDataTable.ParsingOptions = ParsingOptions()
) throws
```

## Parameters 

`url`  

The URL of the JSON or CSV file to import.

`options`  

The parsing options to use when importing a CSV file; ignored when importing JSON files.

## Mentioned in 

Creating a Text Classifier Model

## Discussion

Use this initializer to create a data table from either a JavaScript Object Notation (JSON) file or a comma-separated values (CSV) file. Use `options` to customize how the data table imports information from your CSV file. The data table ignores the `options` parameter when importing JSON files.

## Create a Table from a JSON File

This initializer imports data from a JSON file and creates a row from each dictionary in the root JSON array. The data table names its columns with the dictionary’s keys.

For example, to create a data table as shown above, build a JSON file with a root array of dictionaries that all use the same set of keys.

```
/*
 books.json file:
 [
     {
         "Title": "Alice in Wonderland",
         "Author": "Lewis Carroll",
         "Pages": 124,
         "Genre": "Fantasy"
     },
     {
         "Title": "Hamlet",
         "Author": "William Shakespeare",
         "Pages": 98,
         "Genre": "Drama"
     },
     {
         "Title": "Treasure Island",
         "Author": "Robert L. Stevenson",
         "Pages": 280,
         "Genre": "Adventure"
     },
     {
         "Title": "Peter Pan",
         "Author": "J. M. Barrie",
         "Pages": 94,
         "Genre": "Fantasy"
     }
 ]
 */

let jsonUrl = URL(fileURLWithPath: "books.json")
```

Then, use init(contentsOf:options:) to create the data table.

```
let bookTable = try MLDataTable(contentsOf: jsonUrl)
```

Each entry in JSON array becomes a row in the data table. The set of keys in the JSON dictionaries become the column names in the data table.

## Create a Table from a CSV File

This initializer imports data from a CSV file and creates a row from each line in the CSV file. You can create a CSV file programmatically or use an app like Numbers to export a spreadsheet.

For best results, provide your own parsing options configured to match your CSV file, especially if it has a custom format. See MLDataTable.ParsingOptions for the full list of CSV import customization options.

If you don’t provide parsing options, it is assumed that your CSV file has the following formatting attributes:

- The first entry is a header row with the names of the columns. - Data fields are separated by a comma (`,`). - Each row ends with a newline character (`\n`). - Special characters are escaped with a leading backslash (`\`). - Every quote literal (`"`) is represented by two consecutive quotes (`""`).

For example, to create a data table as shown above, first create a CSV file programmatically or use a spreadsheet app like Numbers to export one, and add it to your project.

```
/*
 books.csv file:
 This example skips these first 3 rows, starting with this one.
 Use skipRows to ignore any lines above the data.

 Title,Author,Pages,Genre
 Alice in Wonderland,Lewis Carroll,124,Fantasy
 Hamlet,William Shakespeare,98,Drama
 Treasure Island,Robert L. Stevenson,280,Adventure
 Peter Pan,J. M. Barrie,94,Fantasy
 */

let csvURL = URL(fileURLWithPath: "books.csv")
```

Then, configure your parsing options to match the format of your CSV file. In this example, the initializer must ignore the first three lines of the CSV file beginning with “This example…”.

```
// Configure CSV file parsing options
var parsingOptions = MLDataTable.ParsingOptions()
parsingOptions.skipRows = 3
parsingOptions.containsHeader = true
parsingOptions.delimiter = ","
parsingOptions.lineTerminator = "\n"
```

Lastly, use init(contentsOf:options:) to create the data table.

```
let bookTable = try MLDataTable(contentsOf: csvURL, options: parsingOptions)
```

The header row becomes the column names in the data table. If the CSV file doesn’t have a header row, the column names become “X1”, “X2”, etc. Each subsequent line of the CSV file becomes a row in the data table.

## Topics

### Parsing options

struct ParsingOptions

The options for parsing a comma-separated values (CSV) file into a data table for a machine learning model.

## See Also

### Related Documentation

Creating a text classifier model

Train a machine learning model to classify natural language text.

### Creating a data table

Creating a Model from Tabular Data

Train a machine learning model by using Core ML to import and manage tabular data.

init(dictionary: [String : any MLDataValueConvertible]) throws

Creates a data table from a dictionary of column names and data values.

init(namedColumns: [String : MLUntypedColumn]) throws

Creates a data table from a dictionary of column names and untyped columns.

init()

Creates an empty table containing no rows or columns.

