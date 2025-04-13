

- Swift
- RegexComponent
-  iso8601 

Type Property

# iso8601

A regex component that matches a default ISO 8601-formatted date string, capturing it as a Foundation date.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
static var iso8601: Date.ISO8601FormatStyle { get }
```

Available when `Self` is `Date.ISO8601FormatStyle`.

## Discussion

This property matches date substrings in accordance with the formatting of Foundation’s Date.ISO8601FormatStyle. This matches the default format of the ISO 8601 format style.

The following example creates a Regex that matches a date formatted with the base ISO 8601 format. It then matches this regex against a source string containing a date and time with this format (using the default UTC time zone, which `Z` indicates), some whitespace, a substring, more whitespace, and a currency value.

```
let iso860Source = "2022-07-14T21:10:15Z   Lemon-lime slushie      $1.99"
let matcher = Regex {
    Capture {
        One(.iso8601)
    }
    OneOrMore(.horizontalWhitespace)
    OneOrMore(.any)
    OneOrMore(.horizontalWhitespace)
    One(.localizedCurrency(code:Locale.Currency("USD"),
                           locale:Locale(identifier: "en_US")))
}
let match = iso860Source.firstMatch(of: matcher)
let date = match?.1 // date == Jul 14, 2022 at 2:10 PM PST
```

## See Also

### Matching dates and times

static func date(Date.FormatStyle.DateStyle, locale: Locale, timeZone: TimeZone, calendar: Calendar?) -> Date.ParseStrategy

Creates a regex component that matches a localized date string formatted in accordance with a style, capturing it as a Foundation date.

static func date(format: Date.FormatString, locale: Locale, timeZone: TimeZone, calendar: Calendar?, twoDigitStartDate: Date) -> Self

Creates a regex component that matches a localized date string formatted in accordance with a format string, capturing it as a Foundation date.

static func dateTime(date: Date.FormatStyle.DateStyle, time: Date.FormatStyle.TimeStyle, locale: Locale, timeZone: TimeZone, calendar: Calendar?) -> Date.ParseStrategy

Creates a regex component that matches a localized date and time string, capturing it as a Foundation date.

static func iso8601Date(timeZone: TimeZone, dateSeparator: Date.ISO8601FormatStyle.DateSeparator) -> Self

Creates a regex component that matches an ISO 8601-formatted date string, capturing it as a Foundation date in the specified time zone.

static func iso8601(timeZone: TimeZone, includingFractionalSeconds: Bool, dateSeparator: Date.ISO8601FormatStyle.DateSeparator, dateTimeSeparator: Date.ISO8601FormatStyle.DateTimeSeparator, timeSeparator: Date.ISO8601FormatStyle.TimeSeparator) -> Self

Creates a regex component that matches an ISO 8601-formatted date string, capturing the matched substring as a Foundation date in the specified time zone.

static func iso8601WithTimeZone(includingFractionalSeconds: Bool, dateSeparator: Date.ISO8601FormatStyle.DateSeparator, dateTimeSeparator: Date.ISO8601FormatStyle.DateTimeSeparator, timeSeparator: Date.ISO8601FormatStyle.TimeSeparator, timeZoneSeparator: Date.ISO8601FormatStyle.TimeZoneSeparator) -> Self

Creates a regex component that matches an ISO 8601-formatted date string that includes a time zone component, capturing the matched substring as a Foundation date.

