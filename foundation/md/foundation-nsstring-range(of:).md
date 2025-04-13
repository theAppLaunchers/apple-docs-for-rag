

- Foundation
- NSString
-  range(of:) 

Instance Method

# range(of:)

Finds and returns the range of the first occurrence of a given string within the string.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func range(of searchString: String) -> NSRange
```

## Parameters 

`searchString`  

The string to search for.

## Return Value

An `NSRange` structure giving the location and length in the receiver of the first occurrence of `searchString`. Returns ``` {``NSNotFound``, 0} ``` if `searchString` is not found or is empty (`""`).

## Discussion

Invokes range(of:options:) with no options.

`NSString` objects are compared by checking the Unicode canonical equivalence of their code point sequences. The length of the returned range and that of `searchString` may differ if equivalent composed character sequences are matched.

Important

When working with text that’s presented to the user, use the localizedStandardRange(of:) method instead.

## See Also

### Finding Characters and Substrings

func contains(String) -> Bool

Returns a Boolean value indicating whether the string contains a given string by performing a case-sensitive, locale-unaware search.

func localizedCaseInsensitiveContains(String) -> Bool

Returns a Boolean value indicating whether the string contains a given string by performing a case-insensitive, locale-aware search.

func localizedStandardContains(String) -> Bool

Returns a Boolean value indicating whether the string contains a given string by performing a case and diacritic insensitive, locale-aware search.

func rangeOfCharacter(from: CharacterSet) -> NSRange

Finds and returns the range in the string of the first character from a given character set.

func rangeOfCharacter(from: CharacterSet, options: NSString.CompareOptions) -> NSRange

Finds and returns the range in the string of the first character, using given options, from a given character set.

func rangeOfCharacter(from: CharacterSet, options: NSString.CompareOptions, range: NSRange) -> NSRange

Finds and returns the range in the string of the first character from a given character set found in a given range with given options.

func range(of: String, options: NSString.CompareOptions) -> NSRange

Finds and returns the range of the first occurrence of a given string within the string, subject to given options.

func range(of: String, options: NSString.CompareOptions, range: NSRange) -> NSRange

Finds and returns the range of the first occurrence of a given string, within the given range of the string, subject to given options.

func range(of: String, options: NSString.CompareOptions, range: NSRange, locale: Locale?) -> NSRange

Finds and returns the range of the first occurrence of a given string within a given range of the string, subject to given options, using the specified locale, if any.

func localizedStandardRange(of: String) -> NSRange

Finds and returns the range of the first occurrence of a given string within the string by performing a case and diacritic insensitive, locale-aware search.

func enumerateLines((String, UnsafeMutablePointer&lt;ObjCBool>) -> Void)

Enumerates all the lines in the string.

func enumerateSubstrings(in: NSRange, options: NSString.EnumerationOptions, using: (String?, NSRange, NSRange, UnsafeMutablePointer&lt;ObjCBool>) -> Void)

Enumerates the substrings of the specified type in the specified range of the string.

