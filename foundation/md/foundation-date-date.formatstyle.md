

- Foundation
- Date
-  Date.FormatStyle 

Structure

# Date.FormatStyle

A structure that creates a locale-appropriate string representation of a date instance and converts strings of dates and times into date instances.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
struct FormatStyle
```

## Overview

A date format style shares the date and time formatting pattern preferred by the user’s locale for formatting and parsing.

When you want to apply a specific formatting style to a single Date instance, use Date.FormatStyle. For other instances, use the following:

- When working with date representations in ISO 8601 format, use Date.ISO8601FormatStyle.

- To represent an interval between two date instances, use Date.RelativeFormatStyle.

- To represent two dates as a pair, for example to get output that looks like `10/21/1985 1:45 PM - 9/13/2015 6:33 PM`, use Date.IntervalFormatStyle.

### Formatting String Representations of Dates and Times

Date.FormatStyle provides a variety of localized presets and configuration options to create user-visible representations of dates and times from instances of Date.

When displaying a date to a user, use the formatted(date:time:) instance method. Set the date and time styles of the date format style separately, according to your particular needs.

For example, to create a string with a full date and no time representation, set the Date.FormatStyle.DateStyle to complete and the Date.FormatStyle.TimeStyle to omitted. Conversely, to create a string representing only the time for the current locale and time zone, set the date style to omitted and the time style to complete, as the following code illustrates:

```
let birthday = Date()

birthday.formatted(date: .complete, time: .omitted) // Sunday, January 17, 2021
birthday.formatted(date: .omitted, time: .complete) // 4:03:12 p.m. CST
```

The results shown are for locale set to `en_US` and time zone set to `CST`.

You can create string representations of a Date instance with various levels of brevity using preset date and time styles. The following example shows date styles of long, abbreviated, and numeric, and time styles of shortened, standard, and complete:

```
let birthday = Date()

birthday.formatted(date: .long, time: .shortened) // January 17, 2021, 4:03 PM
birthday.formatted(date: .abbreviated, time: .standard) // Jan 17, 2021, 4:03:12 PM
birthday.formatted(date: .numeric, time: .complete) // 1/17/2021, 4:03:12 PM CST

birthday.formatted() // Jan 17, 2021, 4:03 PM
```

The default date style is abbreviated and the default time style is shortened.

For full customization of the string representation of a date, use the formatted(_:) instance method of Date and provide a Date.FormatStyle instance.

You can apply more customization of the date and time components and their representation in your app by appying a series of convenience modifiers to your format style. The following example applies a series of modifiers to the format style to precisely define the formatting of the year, month, day, hour, minute, and timezone components of the resulting string. The ordering of the date and time modifiers has no impact on the string produced.

```
// Call the .formatted method on an instance of Date passing in an instance of Date.FormatStyle.

let birthday = Date()

birthday.formatted(
    Date.FormatStyle()
        .year(.defaultDigits)
        .month(.abbreviated)
        .day(.twoDigits)
        .hour(.defaultDigits(amPM: .abbreviated))
        .minute(.twoDigits)
        .timeZone(.identifier(.long))
        .era(.wide)
        .dayOfYear(.defaultDigits)
        .weekday(.abbreviated)
        .week(.defaultDigits)
) 
// Sun, Jan 17, 2021 Anno Domini (week: 4), 11:18 AM America/Chicago
```

Date.FormatStyle provides a convenient factory variable, `dateTime-1kr57`, used to shorten the syntax when applying date and time modifiers to customize the format, as in the following example:

```
let localeArray = ["en_US", "sv_SE", "en_GB", "th_TH", "fr_BE"]
for localeID in localeArray {
    print(meetingDate.formatted(.dateTime
             .day(.twoDigits)
             .month(.wide)
             .weekday(.short)
             .hour(.conversationalTwoDigits(amPM: .wide))
             .locale(Locale(identifier: localeID))))
}

// Th, November 12, 7 PM
// to 12 november 19
// Th 12 November, 19
// พฤ. 12 พฤศจิกายน 19
// je 12 novembre, 19 h
```

### Parsing Dates and Times

To parse a Date instance from an input string, use a date parse strategy. For example:

```
let inputString = "Archive for month 8, archived on day 23 - complete."
let strategy = Date.ParseStrategy(format: "Archive for month \(month: .defaultDigits), archived on day \(day: .twoDigits) - complete.", locale: Locale(identifier: "en_US"), timeZone: TimeZone(abbreviation: "CDT")!)
if let date = try? Date(inputString, strategy: strategy) {
   print(date.formatted()) // "Aug 23, 2000 at 12:00 AM"
}
```

The time defaults to midnight local time unless explicitly defined.

The parse instance method attempts to parse a provided string into an instance of date using the source date format style. The function throws an error if it can’t parse the input string into a date instance.

You can use Date.FormatStyle for round-trip formatting and parsing in a locale-aware manner. This date format style guides parsing the date instance from an input string, as the following code demonstrates:

```
let birthdayFormatStyle = Date.FormatStyle()
    .year(.defaultDigits)
    .month(.abbreviated)
    .day(.twoDigits)
    .hour(.defaultDigits(amPM: .abbreviated))
    .minute(.twoDigits)
    .timeZone(.identifier(.long))
    .era(.abbreviated)
    .weekday(.abbreviated)

let yourBirthdayString = "Mon, Feb 17, 1997 AD, 1:27 AM America/Chicago"

// Create a date instance from a string representation of a date.
let yourBirthday = try? birthdayFormatStyle.parse(yourBirthdayString)
// Feb 17, 1997 at 1:27 AM

```

The following round-trip date formatting example uses a date format style to create a locale-aware string representation of a date instance. Then, the date format style guides parsing the newly created string into a new date instance.

```
let myFormat = Date.FormatStyle()
    .year()
    .day()
    .month()
    .locale(Locale(identifier: "en_US"))

let dateString = Date().formatted(myFormat)
// "Feb 17, 2021" for the "en_US" locale

print(dateString) // Feb 17, 2021

if let anniversary = try? Date(dateString, strategy: myFormat) {
    print(anniversary.formatted(myFormat)) // Feb 17, 2021
    print(anniversary.formatted()) // 2/17/2021, 12:00 AM
} else {
    print("Can't parse string into date with this format.")
}
```

After this code executes, `anniversary` contains a Date instance parsed from `dateString`.

### Applying Format Styles Repeatedly

Once you create a date format style, you can use it to format dates multiple times.

You can use a format style to parse a set of date instances from a set of string representations of dates. Then, use another format style, applied repeatedly, to produce more detailed string representations of those dates for a different locale. For example:

```
func formatIntroDates() {
   let inputFormat = Date.FormatStyle()
      .locale(Locale(identifier: "en_GB"))
      .year()
      .month()
      .day()
    // Parse string inputs into date instances.
    guard let productIntroDate = try? Date("9 Jan 2007", strategy: inputFormat) else { return }
    guard let anotherIntroDate = try? Date("27 Jan 2010", strategy: inputFormat) else { return }
    guard let conferenceDate = try? Date("7 Jun 2021", strategy: inputFormat) else { return }

    let outputFormat = Date.FormatStyle() // Define format style for string output.
        .locale(Locale(identifier: "en_US"))
        .year()
        .month(.wide)
        .day(.twoDigits)
        .weekday(.abbreviated)

    // Apply the output format on the three dates below.
    print(outputFormat.format(conferenceDate)) // Mon, June 07, 2021
    print(outputFormat.format(anotherIntroDate)) // Wed, January 27, 2010
    print(outputFormat.format(productIntroDate)) // Tue, January 09, 2007
}
```

## Topics

### Creating a Date Format Style

init(date: Date.FormatStyle.DateStyle?, time: Date.FormatStyle.TimeStyle?, locale: Locale, calendar: Calendar, timeZone: TimeZone, capitalizationContext: FormatStyleCapitalizationContext)

Creates an instance using the provided date, time, locale, calendar, time zone, and capitalization context.

### Specifying the Date Format

func day(Date.FormatStyle.Symbol.Day) -> Date.FormatStyle

Modifies the date format style to use the specified day format style.

func dayOfYear(Date.FormatStyle.Symbol.DayOfYear) -> Date.FormatStyle

Modifies the date format style to use the specified day of the year format style.

func era(Date.FormatStyle.Symbol.Era) -> Date.FormatStyle

Modifies the date format style to use the specified era format style.

func month(Date.FormatStyle.Symbol.Month) -> Date.FormatStyle

Modifies the date format style to use the specified month format style.

func quarter(Date.FormatStyle.Symbol.Quarter) -> Date.FormatStyle

Modifies the date format style to use the specified quarter format style.

func week(Date.FormatStyle.Symbol.Week) -> Date.FormatStyle

Modifies the date format style to use the specified week format style.

func weekday(Date.FormatStyle.Symbol.Weekday) -> Date.FormatStyle

Modifies the date format style to use the specified weekday format style.

func year(Date.FormatStyle.Symbol.Year) -> Date.FormatStyle

Modifies the date format style to use the specified year format style.

struct DateStyle

Type that defines date styles varied in length or components included.

### Specifying the Time Format

func hour(Date.FormatStyle.Symbol.Hour) -> Date.FormatStyle

Modifies the date format style to use the specified hour format style.

func minute(Date.FormatStyle.Symbol.Minute) -> Date.FormatStyle

Modifies the date format style to use the specified minute format style.

func second(Date.FormatStyle.Symbol.Second) -> Date.FormatStyle

Modifies the date format style to use the specified second format style.

func secondFraction(Date.FormatStyle.Symbol.SecondFraction) -> Date.FormatStyle

Modifies the date format style to use the specified second fraction format style.

func timeZone(Date.FormatStyle.Symbol.TimeZone) -> Date.FormatStyle

Modifies the date format style to use the specified time zone format style.

struct TimeStyle

Type that defines time styles varied in length or components included.

### Modifying a Date Format Style

var timeZone: TimeZone

The time zone to use when formatting the date and time components.

var calendar: Calendar

The calendar to use when formatting the date.

var capitalizationContext: FormatStyleCapitalizationContext

The capitalization context to use when formatting the date.

var locale: Locale

The locale to use when formatting the date and time components.

### Applying Visual Attributes to Dates

var attributed: Date.AttributedStyle

An attributed format style created from the date format style.

Deprecated

struct AttributedStyle

A structure that creates a locale-appropriate attributed string representation of a date instance.

Deprecated

### Parsing Dates

struct ParseStrategy

### Comparing Date Format Styles

static func != (Self, Self) -> Bool

Returns a Boolean value indicating whether two values are not equal.

static func == (Date, Date) -> Bool

Returns true if the two `Date` values represent the same point in time.

### Supporting Symbols

struct Symbol

Types that customize formatting templates either by using the date format style’s modifier functions or by constructing fixed-pattern date format strings.

### Structures

struct Attributed

### Instance Properties

var attributedStyle: Date.FormatStyle.Attributed

## Relationships

### Conforms To

- Copyable
- CustomConsumingRegexComponent
- Decodable
- DiscreteFormatStyle
- Encodable
- Equatable
- FormatStyle
- Hashable
- ParseStrategy
- ParseableFormatStyle
- RegexComponent
- Sendable

## See Also

### Applying date and time styles

static var dateTime: Date.FormatStyle

A style for formatting a date and time.

static var iso8601: Date.ISO8601FormatStyle

A style for formatting a date in accordance with the ISO-8601 standard.

struct ISO8601FormatStyle

A type that converts between dates and their ISO-8601 string representations.

static func verbatim(Date.FormatString, locale: Locale?, timeZone: TimeZone, calendar: Calendar) -> Date.VerbatimFormatStyle

Returns a style for formatting a date with an explicitly-specified style.

struct VerbatimFormatStyle

A style that formats a date with an explicitly-specified style.

static var interval: Date.IntervalFormatStyle

A style for formatting a date interval.

struct IntervalFormatStyle

A format style that creates string representations of date intervals.

static func relative(presentation: Date.RelativeFormatStyle.Presentation, unitsStyle: Date.RelativeFormatStyle.UnitsStyle) -> Self

Returns a style for formatting a date as relative to the current date.

struct RelativeFormatStyle

A format style that forms locale-aware string representations of a relative date or time.

static func components(style: Date.ComponentsFormatStyle.Style, fields: Set&lt;Date.ComponentsFormatStyle.Field>?) -> Self

Returns a style for formatting a date interval in terms of specific date components.

struct ComponentsFormatStyle

A style for formatting a date interval in terms of specific date components.

