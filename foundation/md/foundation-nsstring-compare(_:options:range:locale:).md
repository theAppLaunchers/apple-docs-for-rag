

- Foundation
- NSString
-  compare(\_:options:range:locale:) 

Instance Method

# compare(\_:options:range:locale:)

Compares the string using the specified options and returns the lexical ordering for the range.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func compare(
    _ string: String,
    options mask: NSString.CompareOptions = [],
    range rangeOfReceiverToCompare: NSRange,
    locale: Any?
) -> ComparisonResult
```

## Parameters 

`string`  

The string with which to compare the range of the receiver specified by `range`.

This value must not be `nil`. If this value is `nil`, the behavior is undefined and may change in future versions of macOS.

`mask`  

Options for the search—you can combine any of the following using a C bitwise OR operator: `NSCaseInsensitiveSearch`, `NSLiteralSearch`, `NSNumericSearch`.

See String Programming Guide for details on these options.

`rangeOfReceiverToCompare`  

The range of the receiver over which to perform the comparison. The range must not exceed the bounds of the receiver.

Important

Raises an `NSRangeException` if `range` exceeds the bounds of the receiver.

`locale`  

An instance of NSLocale. To use the current locale, pass \[NSLocale current\]. For example, if you are comparing strings to present to the end-user, use the current locale. To use the system locale, pass `nil`.

## Return Value

Returns an ComparisonResult value that indicates the lexical ordering of a specified range within the receiver and a given string. ComparisonResult.orderedAscending if the substring of the receiver given by `range` precedes `aString` in lexical ordering for the locale given in `dict`, ComparisonResult.orderedSame if the substring of the receiver and `aString` are equivalent in lexical value, and ComparisonResult.orderedDescending if the substring of the receiver follows `aString`.

## Discussion

The `locale` argument affects both equality and ordering algorithms. For example, in some locales, accented characters are ordered immediately after the base; other locales order them after “z”.

## See Also

### Identifying and Comparing Strings

func caseInsensitiveCompare(String) -> ComparisonResult

Returns the result of invoking compare(_:options:) with `NSCaseInsensitiveSearch` as the only option.

func localizedCaseInsensitiveCompare(String) -> ComparisonResult

Compares the string with a given string using a case-insensitive, localized, comparison.

func compare(String) -> ComparisonResult

Returns the result of invoking compare(_:options:range:) with no options and the receiver’s full extent as the range.

func localizedCompare(String) -> ComparisonResult

Compares the string and a given string using a localized comparison.

func compare(String, options: NSString.CompareOptions) -> ComparisonResult

Compares the string with the specified string using the given options.

func compare(String, options: NSString.CompareOptions, range: NSRange) -> ComparisonResult

Returns the result of invoking compare(_:options:range:locale:) with a `nil` locale.

func localizedStandardCompare(String) -> ComparisonResult

Compares strings as sorted by the Finder.

func hasPrefix(String) -> Bool

Returns a Boolean value that indicates whether a given string matches the beginning characters of the receiver.

func hasSuffix(String) -> Bool

Returns a Boolean value that indicates whether a given string matches the ending characters of the receiver.

func isEqual(to: String) -> Bool

Returns a Boolean value that indicates whether a given string is equal to the receiver using a literal Unicode-based comparison.

var hash: Int

An unsigned integer that can be used as a hash table address.

struct CompareOptions

These values represent the options available to many of the string classes’ search and comparison methods.

struct EncodingConversionOptions

Options for converting string encodings.

