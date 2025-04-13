

- Foundation
- JSONSerialization
- JSONSerialization.ReadingOptions
-  topLevelDictionaryAssumed 

Type Property

# topLevelDictionaryAssumed

Specifies that the parser assumes the top level of the JSON data is a dictionary, even if it doesn’t begin and end with curly braces.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
static var topLevelDictionaryAssumed: JSONSerialization.ReadingOptions { get }
```

## Discussion

This is an extension to JSON5 that isn’t part of the specification. AttributedString uses this option, along with json5Allowed, to support the use of JSON5 inside Markdown strings that use multiple custom attributes. Using topLevelDictionaryAssumed allows for the following syntax in the parentheses of the custom attribute markup:

```
This is a [Markdown](https://commonmark.org) string with a ^[custom attribute](factor: 10, other: true).
```

Without topLevelDictionaryAssumed, the markup would have to use explicit enclosing braces to declare the contents of the parentheses to be a dictionary:

```
This is a [Markdown](https://commonmark.org) string with a ^[custom attribute]({factor: 10, other: true}).
```

When you use braces, you must use matched pairs. This means that with topLevelDictionaryAssumed set, the syntax `({…})` and `(…)` are both legal, but `({…)` and `(…})` are not.

## See Also

### Reading Options

static var mutableContainers: JSONSerialization.ReadingOptions

Specifies that arrays and dictionaries in the returned object are mutable.

static var mutableLeaves: JSONSerialization.ReadingOptions

Specifies that leaf strings in the JSON object graph are mutable.

static var fragmentsAllowed: JSONSerialization.ReadingOptions

Specifies that the parser allows top-level objects that aren’t arrays or dictionaries.

static var json5Allowed: JSONSerialization.ReadingOptions

Specifies that reading serialized JSON data supports the JSON5 syntax.

static var allowFragments: JSONSerialization.ReadingOptions

A deprecated option that specifies that the parser should allow top-level objects that aren’t arrays or dictionaries.

Deprecated

static var mutableContainers: JSONSerialization.ReadingOptions

Specifies that arrays and dictionaries in the returned object are mutable.

static var mutableLeaves: JSONSerialization.ReadingOptions

Specifies that leaf strings in the JSON object graph are mutable.

static var fragmentsAllowed: JSONSerialization.ReadingOptions

Specifies that the parser allows top-level objects that aren’t arrays or dictionaries.

static var json5Allowed: JSONSerialization.ReadingOptions

Specifies that reading serialized JSON data supports the JSON5 syntax.

static var allowFragments: JSONSerialization.ReadingOptions

A deprecated option that specifies that the parser should allow top-level objects that aren’t arrays or dictionaries.

Deprecated

