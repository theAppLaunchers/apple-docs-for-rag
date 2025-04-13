

- Foundation
- NumberFormatter
-  getObjectValue(\_:for:range:) 

Instance Method

# getObjectValue(\_:for:range:)

Returns by reference a cell-content object after creating it from a range of characters in a given string.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func getObjectValue(
    _ obj: AutoreleasingUnsafeMutablePointer?,
    for string: String,
    range rangep: UnsafeMutablePointer?
) throws
```

## Parameters 

`obj`  

On return, contains an instance of NSDecimalNumber or NSNumber based on the current value of the generatesDecimalNumbers property. Returns `nil` by reference if conversion failed.

`string`  

A string object with the range of characters specified in `rangep` that is used to create `anObject`.

`rangep`  

A range of characters in `aString`. On return, contains the actual range of characters used to create the object.

## Discussion

If a string contains any characters other than numerical digits or locale-appropriate group or decimal separators, parsing will fail.

Any leading or trailing space separator characters in a string are ignored. For example, the strings “ 5”, “5 “, and “5” all produce the number `5`.

If there is an error, this method calls `control(_:didFailToFormatString:errorDescription:)` on the delegate.

Handling Errors in Swift

In Swift, this method returns `Void` and is marked with the `throws` keyword to indicate that it throws an error in cases of failure.

You call this method in a `try` expression and handle any errors in the `catch` clauses of a `do` statement, as described in Error Handling in The Swift Programming Language and `About Imported Cocoa Error Parameters`.

## See Also

### Converting Between Numbers and Strings

func number(from: String) -> NSNumber?

Returns an NSNumber object created by parsing a given string.

func string(from: NSNumber) -> String?

Returns a string containing the formatted value of the provided number object.

class func localizedString(from: NSNumber, number: NumberFormatter.Style) -> String

Returns a localized number string with the specified style.

