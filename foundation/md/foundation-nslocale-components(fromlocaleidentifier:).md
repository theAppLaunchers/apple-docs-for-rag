

- Foundation
- NSLocale
-  components(fromLocaleIdentifier:) 

Type Method

# components(fromLocaleIdentifier:)

Returns a dictionary that is the result of parsing a locale ID.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
class func components(fromLocaleIdentifier string: String) -> [String : String]
```

## Parameters 

`string`  

A locale ID, consisting of language, script, country, variant, and keyword/value pairs, for example, `"en_US@calendar=japanese"`.

## Return Value

A dictionary that is the result of parsing `string` as a locale ID. The keys are the constant NSString constants corresponding to the locale ID components, and the values correspond to constants where available. For possible values, see NSLocale.Key.

## Discussion

For example, the locale identifier `"en_US@calendar=japanese"` yields a dictionary with three entries:

- languageCode = `en`

- countryCode = `US`

- calendar = NSJapaneseCalendar

## See Also

### Converting Between Identifiers

class func canonicalLocaleIdentifier(from: String) -> String

Returns the canonical identifier for a given locale identification string.

class func localeIdentifier(fromComponents: [String : String]) -> String

Returns a locale identifier from the components specified in a given dictionary.

class func canonicalLanguageIdentifier(from: String) -> String

Returns a canonical language identifier by mapping an arbitrary locale identification string to the canonical identifier.

class func localeIdentifier(fromWindowsLocaleCode: UInt32) -> String?

Returns a locale identifier from a Windows locale code.

class func windowsLocaleCode(fromLocaleIdentifier: String) -> UInt32

Returns a Window locale code from the locale identifier.

