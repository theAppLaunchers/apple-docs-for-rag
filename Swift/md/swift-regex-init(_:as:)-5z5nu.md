

- Swift
- Regex
-  init(\_:as:) 

Initializer

# init(\_:as:)

Creates a regular expression from the given string, using the specified capture type.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
init(
    _ pattern: String,
    as outputType: Output.Type = Output.self
) throws
```

## Parameters 

`pattern`  

A string with regular expression syntax.

`outputType`  

The desired type for the output captures.

## Discussion

You can use this initializer to create a `Regex` instance from a regular expression that you have stored in `pattern` when you know the capture structure of the regular expression in advance.

In this example, the regular expression includes two parenthesized capture groups, so the capture type is `(Substring, Substring, Substring)`. The first substring in the tuple represents the entire match, while the second and third substrings represent the first and second capture group, respectively.

```
let keyAndValue = try Regex("(.+): (.+)", as: (Substring, Substring, Substring).self)
```

This initializer throws an error if `pattern` uses invalid regular expression syntax, or if `outputType` does not match the capture structure declared by `pattern`. If you don’t know the capture structure in advance, use the `init(_:)` initializer instead.

