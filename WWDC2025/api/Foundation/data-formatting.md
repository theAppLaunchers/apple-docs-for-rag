Collection

*   [Foundation](/documentation/foundation)
*   Data Formatting

API Collection

# Data Formatting

Convert numbers, dates, measurements, and other values to and from locale-aware string representations.

## [Overview](/documentation/Foundation/data-formatting#overview)

Foundation supports two approaches for data formatting:

*   When working in Swift, use `formatted` methods directly on the types you want to format, optionally using [`FormatStyle`](/documentation/foundation/formatstyle) and its subtypes to customize formatter output. This approach supports dates, integers, floating-point numbers, measurements, sequences, and person name components. Foundation caches identically-configured formatter instances internally, allowing you to focus on your app’s formatting needs.
    
*   In Objective-C, create instances of [`Formatter`](/documentation/foundation/formatter) and its subtypes, and use the [`string(for:)`](/documentation/foundation/formatter/string\(for:\)) method to convert objects to formatted strings.
    

## [Topics](/documentation/Foundation/data-formatting#topics)

### [Data formatting in Swift](/documentation/Foundation/data-formatting#Data-formatting-in-Swift)

[

Language Introspector](/documentation/foundation/language-introspector)

Converts data into human-readable text using formatters and locales.

```swift
```swift
```swift
protocol FormatStyle
```
```

A type that converts a given data type into a representation in another type, such as a string.
```
```swift
```swift
```swift
struct IntegerFormatStyle
```
```

A structure that converts between integer values and their textual representations.
```
```swift
```swift
```swift
struct FloatingPointFormatStyle
```
```

A structure that converts between floating-point values and their textual representations.
```
```swift
```swift
```swift
struct FormatStyle
```
```

A structure that converts between decimal values and their textual representations.
```
```swift
```swift
```swift
struct ListFormatStyle
```
```

A type that formats lists of items with a separator and conjunction appropriate for a given locale.
```
```swift
```swift
```swift
struct StringStyle
```
```
```
```swift
```swift
```swift
struct FormatStyle
```
```

A structure that converts between URL instances and their textual representations.
```
```swift
```swift
```swift
struct FormatStyleCapitalizationContext
```
```

The capitalization formatting context used when formatting dates and times.
```

[

API Reference

Format Style Configurations](/documentation/foundation/format-style-configurations)

Behaviors for traits like numeric precision, rounding, and scale, used for formatting and parsing numeric values.

### [Data parsing in Swift](/documentation/Foundation/data-formatting#Data-parsing-in-Swift)

```swift
```swift
```swift
```swift
protocol ParseableFormatStyle
```
```

A type that can convert a given input data type into a representation in an output type.
```
```swift
```swift
```swift
protocol ParseStrategy
```
```

A type that parses an input representation, such as a formatted string, into a provided data type.
```
```swift
```swift
```swift
struct IntegerParseStrategy
```
```

A parse strategy for creating integer values from formatted strings.
```
```swift
```swift
```swift
struct FloatingPointParseStrategy
```
```

A parse strategy for creating floating-point values from formatted strings.
```
```swift
```swift
```swift
struct ParseStrategy
```
```

A parse strategy for creating decimal values from formatted strings.
```
```

### [Numbers and currency](/documentation/Foundation/data-formatting#Numbers-and-currency)

```swift
```swift
```swift
```swift
class NumberFormatter
```
```

A formatter that converts between numeric values and their textual representations.
```
```

### [Names](/documentation/Foundation/data-formatting#Names)

```swift
```swift
```swift
```swift
class PersonNameComponentsFormatter
```
```

A formatter that provides localized representations of the components of a person’s name.
```
```swift
```swift
```swift
struct PersonNameComponents
```
```

The separate parts of a person’s name, allowing locale-aware formatting.
```
```

### [Dates and times](/documentation/Foundation/data-formatting#Dates-and-times)

```swift
```swift
```swift
```swift
class DateFormatter
```
```

A formatter that converts between dates and their textual representations.
```
```swift
```swift
```swift
class DateComponentsFormatter
```
```

A formatter that creates string representations of quantities of time.
```
```swift
```swift
```swift
class RelativeDateTimeFormatter
```
```

A formatter that creates locale-aware string representations of a relative date or time.
```
```swift
```swift
```swift
class DateIntervalFormatter
```
```

A formatter that creates string representations of time intervals.
```
```swift
```swift
```swift
class ISO8601DateFormatter
```
```

A formatter that converts between dates and their ISO 8601 string representations.
```
```

### [Data sizes](/documentation/Foundation/data-formatting#Data-sizes)

```swift
```swift
```swift
```swift
class ByteCountFormatter
```
```

A formatter that converts a byte count value into a localized description that is formatted with the appropriate byte modifier (KB, MB, GB and so on).
```
```

### [Measurements](/documentation/Foundation/data-formatting#Measurements)

```swift
```swift
```swift
```swift
class MeasurementFormatter
```
```

A formatter that provides localized representations of units and measurements.
```
```

### [Lists](/documentation/Foundation/data-formatting#Lists)

```swift
```swift
```swift
```swift
class ListFormatter
```
```

An object that provides locale-correct formatting of a list of items using the appropriate separator and conjunction.
```
```

### [Internationalization](/documentation/Foundation/data-formatting#Internationalization)

```swift
```swift
```swift
```swift
struct Locale
```
```

Information about linguistic, cultural, and technological conventions for use in formatting data for presentation.
```
```

### [Custom formatters](/documentation/Foundation/data-formatting#Custom-formatters)

```swift
```swift
```swift
```swift
class Formatter
```
```

An abstract class that declares an interface for objects that create, interpret, and validate the textual representation of values.
```
```

### [Automatic grammar agreement](/documentation/Foundation/data-formatting#Automatic-grammar-agreement)

```swift
```swift
```swift
```swift
enum InflectionRule
```
```

A rule that affects how an attributed string performs automatic grammatical agreement.
```
```swift
```swift
```swift
struct Morphology
```
```

A description of the grammatical properties of a string.
```
```swift
```swift
```swift
struct TermOfAddress
```
```

The type for representing grammatical gender in localized text.
```
```swift
```swift
```swift
enum InflectionConcept
```
```

An inflection method to use when localizing text.
```
```swift
```swift
```swift
struct Pronoun
```
```

A custom pronoun for referring to a third person.
```
```

### [Deprecated](/documentation/Foundation/data-formatting#Deprecated)

```swift
```swift
```swift
```swift
class LengthFormatter
```
```

A formatter that provides localized descriptions of linear distances, such as length and height measurements.
```
```swift
```swift
```swift
class MassFormatter
```
```

A formatter that provides localized descriptions of mass and weight values.
```
```swift
```swift
```swift
class EnergyFormatter
```
```

A formatter that provides localized descriptions of energy values.
```
```

## [See Also](/documentation/Foundation/data-formatting#see-also)

### [Fundamentals](/documentation/Foundation/data-formatting#Fundamentals)

[

API Reference

Numbers, Data, and Basic Values](/documentation/foundation/numbers-data-and-basic-values)

Work with primitive values and other fundamental types used throughout Cocoa.

[

API Reference

Strings and Text](/documentation/foundation/strings-and-text)

Create and process strings of Unicode characters, use regular expressions to find patterns, and perform natural language analysis of text.

[

API Reference

Collections](/documentation/foundation/collections)

Use arrays, dictionaries, sets, and specialized collections to store and iterate groups of objects or values.

[

API Reference

Dates and Times](/documentation/foundation/dates-and-times)

Compare dates and times, and perform calendar and time zone calculations.

[

API Reference

Units and Measurement](/documentation/foundation/units-and-measurement)

Label numeric quantities with physical dimensions to allow locale-aware formatting and conversion between related units.

[

API Reference

Filters and Sorting](/documentation/foundation/filters-and-sorting)

Use predicates, expressions, and sort descriptors to examine elements in collections and other services.