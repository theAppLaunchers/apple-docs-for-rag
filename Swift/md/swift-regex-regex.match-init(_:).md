

- Swift
- Regex
- Regex.Match
-  init(\_:) 

Initializer

# init(\_:)

Creates a regular expression match with a dynamic capture list from the given match.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
init(_ match: Regex.Match)
```

Available when `Output` is `AnyRegexOutput`.

## Parameters 

`match`  

A regular expression match to convert to a match with type-erased captures.

## Discussion

You can use this initializer to convert a `Regex.Match` with strongly-typed captures into a match with the type-eraser `AnyRegexOutput` as its output type.

