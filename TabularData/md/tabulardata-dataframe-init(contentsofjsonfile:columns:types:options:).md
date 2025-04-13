

- TabularData
- DataFrame
-  init(contentsOfJSONFile:columns:types:options:) 

Initializer

# init(contentsOfJSONFile:columns:types:options:)

Creates a data frame by reading a JSON file.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
init(
    contentsOfJSONFile url: URL,
    columns: [String]? = nil,
    types: [String : JSONType] = [:],
    options: JSONReadingOptions = .init()
) throws
```

## Parameters 

`url`  

A URL to a JSON file.

`columns`  

An array of column names; Set to `nil` to use every column in the JSON file.

`types`  

A dictionary of column names and their JSON types. The data frame infers the types for column names that aren’t in the dictionary.

`options`  

The options that instruct how the data frame reads the JSON file.

## Discussion

The JSON file should contain a sequence of objects where each object contains a value for every column name. Here’s an example with two columns “id” and “name”:

```
[
  {"id": 1, "name": "foo"},
  {"id": 2, "name": "bar"},
]
```

Throws

A `JSONReadingError` instance.

## See Also

### Creating a Data Frame from a JSON File

init(jsonData: Data, columns: [String]?, types: [String : JSONType], options: JSONReadingOptions) throws

Creates a data frame by converting JSON data.

enum JSONType

Represents the value types in a JSON file.

struct JSONReadingOptions

A set of JSON file-reading options.

