

- Create ML Components
- ColumnSelectorTransformer
-  init(transformers:columnMapping:) 

Initializer

# init(transformers:columnMapping:)

Creates a select transformer.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 11.0+

``` source
init(
    transformers: [String : Base],
    columnMapping: [String : String] = [:]
)
```

## Parameters 

`transformers`  

A dictionary of column names to transformers.

`columnMapping`  

A mapping of input column names to output column names.

