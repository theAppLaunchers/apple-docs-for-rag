

- AppKit
- NSTextList
-  init(markerFormat:options:) 

Initializer

# init(markerFormat:options:)

Returns an initialized text list.

macOS 10.0+

``` source
convenience init(
    markerFormat: NSTextList.MarkerFormat,
    options: Int
)
```

## Parameters 

`markerFormat`  

The marker format for the text list.

`options`  

The marker options for the text list. Values for `mask` are listed in Constants.

## Return Value

An initialized text list.

## Discussion

The marker format is specified as a constant string, except for a numbering specifier, which takes the form `{`keyword`}`. The currently supported values for keyword include:

- `box`

- `check`

- `circle`

- `diamond`

- `disc`

- `hyphen`

- `square`

- `lower-hexadecimal`

- `upper-hexadecimal`

- `octal`

- `lower-alpha` or `lower-latin`

- `upper-alpha` or `upper-latin`

- `lower-roman`

- `upper-roman`

- `decimal`

Thus, for example, `@"({decimal})"` would specify the format for a list numbered (1), (2), (3), and so on, and `@"{upper-roman}"` would specify the format for a list numbered I, II, III, IV, and so on. (All of these keywords are included in the Cascading Style Sheets level 3 specification.)

## See Also

### Creating a text list

init?(coder: NSCoder)

Initializes and returns a newly allocated text list item.

init(markerFormat: NSTextList.MarkerFormat, options: NSTextList.Options, startingItemNumber: Int)

Returns a new text list with the format, options, and starting item number you provide.

