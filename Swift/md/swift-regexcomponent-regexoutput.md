

- Swift
- RegexComponent
-  RegexOutput 

Associated Type

# RegexOutput

The output type for this regular expression.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
associatedtype RegexOutput
```

**Required**

## Discussion

A `Regex` instance’s output type depends on whether the `Regex` has captures and how it is created.

- A `Regex` created from a string using the `init(_:)` initializer has an output type of AnyRegexOutput, whether it has captures or not.

- A `Regex` without captures created from a regex literal, the `init(_:as:)` initializer, or a `RegexBuilder` closure has a `Substring` output type, where the substring is the portion of the string that was matched.

- A `Regex` with captures created from a regex literal or the `init(_:as:)` initializer has a tuple of substrings as its output type. The first component of the tuple is the full portion of the string that was matched, with the remaining components holding the captures.

## See Also

### Supporting types

typealias DateStyle

A type alias to use when matching date components in a regular expression.

typealias TimeStyle

A type alias to use when matching time components in a regular expression.

