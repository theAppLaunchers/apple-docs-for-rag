

- Foundation
- NSLocale
-  localeIdentifier(fromComponents:) 

Type Method

# localeIdentifier(fromComponents:)

Returns a locale identifier from the components specified in a given dictionary.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
class func localeIdentifier(fromComponents dict: [String : String]) -> String
```

## Parameters 

`dict`  

A dictionary containing components that specify a locale. For possible values, see `NSLocale Component Keys`.

## Return Value

A locale identifier created from the components specified in `dict`.

## Discussion

This reverses the actions of components(fromLocaleIdentifier:), so for example the dictionary `{NSLocaleLanguageCode="en", NSLocaleCountryCode="US", NSLocaleCalendar=NSJapaneseCalendar}` becomes `"en_US@calendar=japanese"`.

## See Also

### Related Documentation

class var isoLanguageCodes: [String]

The list of known language codes.

### Converting Between Identifiers

class func canonicalLocaleIdentifier(from: String) -> String

Returns the canonical identifier for a given locale identification string.

class func components(fromLocaleIdentifier: String) -> [String : String]

Returns a dictionary that is the result of parsing a locale ID.

class func canonicalLanguageIdentifier(from: String) -> String

Returns a canonical language identifier by mapping an arbitrary locale identification string to the canonical identifier.

class func localeIdentifier(fromWindowsLocaleCode: UInt32) -> String?

Returns a locale identifier from a Windows locale code.

class func windowsLocaleCode(fromLocaleIdentifier: String) -> UInt32

Returns a Window locale code from the locale identifier.

