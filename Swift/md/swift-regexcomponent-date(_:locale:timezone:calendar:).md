

- Swift
- RegexComponent
-  date(\_:locale:timeZone:calendar:) 

Type Method

# date(\_:locale:timeZone:calendar:)

Creates a regex component that matches a localized date string formatted in accordance with a style, capturing it as a Foundation date.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
static func date(
    _ style: Date.FormatStyle.DateStyle,
    locale: Locale,
    timeZone: TimeZone,
    calendar: Calendar? = nil
) -> Date.ParseStrategy
```

Available when `Self` is `Date.ParseStrategy`.

## Parameters 

`style`  

A Date.FormatStyle.DateStyle to use when matching date substrings.

`locale`  

The locale to use when matching date substrings. Matching uses this locale to evaluate the order of date components. It also uses the locale’s language for date format styles that use words.

`timeZone`  

The time zone to use when returning a captured Date. The returned date’s time value is `00:00:00` in this time zone.

`calendar`  

The calendar to use when matching date substrings. If `nil`, matching uses the default calendar of the specified `locale`.

## Return Value

A `RegexComponent` that matches date substrings as Foundation Date instances.

## Discussion

This method matches date substrings in accordance with the formatting of Foundation’s Date.FormatStyle.

If a time value follows the date substring, the matcher ignores it, treating it as any other character sequence. To match date and time substrings, use dateTime(date:time:locale:timeZone:calendar:).

The following example creates a Regex that matches a date formatted with the numeric style in the `en_US` locale. It then matches this regex against a source string containing a date with this format, some whitespace, a substring, more whitespace, and a currency value.

```
let source = "7/31/2022  Lemon-lime slushie      $1.99"
let matcher = Regex {
    Capture {
        One(.date(.numeric,
                  locale: Locale(identifier: "en_US"),
                  timeZone: TimeZone(identifier: "PST")!))
    }
}
guard let match = source.firstMatch(of: matcher) else { return }
let date = match.1 // date == Jul 31, 2022 at 12:00 AM PST
```

## See Also

### Matching dates and times

static func date(format: Date.FormatString, locale: Locale, timeZone: TimeZone, calendar: Calendar?, twoDigitStartDate: Date) -> Self

Creates a regex component that matches a localized date string formatted in accordance with a format string, capturing it as a Foundation date.

static func dateTime(date: Date.FormatStyle.DateStyle, time: Date.FormatStyle.TimeStyle, locale: Locale, timeZone: TimeZone, calendar: Calendar?) -> Date.ParseStrategy

Creates a regex component that matches a localized date and time string, capturing it as a Foundation date.

static var iso8601: Date.ISO8601FormatStyle

A regex component that matches a default ISO 8601-formatted date string, capturing it as a Foundation date.

static func iso8601Date(timeZone: TimeZone, dateSeparator: Date.ISO8601FormatStyle.DateSeparator) -> Self

Creates a regex component that matches an ISO 8601-formatted date string, capturing it as a Foundation date in the specified time zone.

static func iso8601(timeZone: TimeZone, includingFractionalSeconds: Bool, dateSeparator: Date.ISO8601FormatStyle.DateSeparator, dateTimeSeparator: Date.ISO8601FormatStyle.DateTimeSeparator, timeSeparator: Date.ISO8601FormatStyle.TimeSeparator) -> Self

Creates a regex component that matches an ISO 8601-formatted date string, capturing the matched substring as a Foundation date in the specified time zone.

static func iso8601WithTimeZone(includingFractionalSeconds: Bool, dateSeparator: Date.ISO8601FormatStyle.DateSeparator, dateTimeSeparator: Date.ISO8601FormatStyle.DateTimeSeparator, timeSeparator: Date.ISO8601FormatStyle.TimeSeparator, timeZoneSeparator: Date.ISO8601FormatStyle.TimeZoneSeparator) -> Self

Creates a regex component that matches an ISO 8601-formatted date string that includes a time zone component, capturing the matched substring as a Foundation date.

