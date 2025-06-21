*   [Foundation](/documentation/foundation)
*   [Locale](/documentation/foundation/locale)
*   Locale.Components

Structure

# Locale.Components

A type that represents the components of a locale, for use when creating a locale with specific overrides.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
struct Components
```
```
```
```
```
```
```
```

## [Overview](/documentation/Foundation/Locale/Components#overview)

Use [`Locale.Components`](/documentation/foundation/locale/components) with the [`init(components:)`](/documentation/foundation/locale/init\(components:\)) initializer to create a custom [`Locale`](/documentation/foundation/locale) that overrides specific traits of a default locale. When you create a locale with components, the locale uses any overridden values instead of defaults preferred by the region or language. Leave a property `nil` to accept the default value.

The properties in this type correspond with those in [`Locale`](/documentation/foundation/locale), which declares them as read-only rather than read-write. You use this type to customize components when creating a custom locale, and use [`Locale`](/documentation/foundation/locale) to examine the components of an existing locale.

The following example creates a [`Locale.Components`](/documentation/foundation/locale/components) instance for US English, but then customizes its components. It sets the first day of the week to Monday and the hour cycle to zero-to-23. These components override the `en-US` defaults of Sunday and one-to-12, respectively. It then uses [`init(components:)`](/documentation/foundation/locale/init\(components:\)) to create a custom [`Locale`](/documentation/foundation/locale).

```swift
```swift
```swift
```swift
```swift
```swift
var components = Locale.Components(languageCode: "en", languageRegion: "US")
```
```
components.firstDayOfWeek = Locale.Weekday.monday
components.hourCycle = Locale.HourCycle.zeroToTwentyThree
```swift
```swift
let locale = Locale(components: components)
```
```
```
```
```
```

## [Topics](/documentation/Foundation/Locale/Components#topics)

### [Creating a locale components instance](/documentation/Foundation/Locale/Components#Creating-a-locale-components-instance)

[`init(identifier: String)`](/documentation/foundation/locale/components/init\(identifier:\))

Creates a locale components instance with the specified identifier.

[`init(languageCode: Locale.LanguageCode?, script: Locale.Script?, languageRegion: Locale.Region?)`](/documentation/foundation/locale/components/init\(languagecode:script:languageregion:\))

Creates a locale components instance with the specified language code, script, and region identifier.

[`init(locale: Locale)`](/documentation/foundation/locale/components/init\(locale:\))

Creates a language components instance from an existing locale.

### [Specifying language components](/documentation/Foundation/Locale/Components#Specifying-language-components)

```swift
```swift
```swift
```swift
var languageComponents: Locale.Language.Components
```
```

The Unicode language identifier part of a locale.
```
```swift
```swift
```swift
struct Components
```
```

A type that identifies a language by its various components.
```
```

### [Specifying date and time components](/documentation/Foundation/Locale/Components#Specifying-date-and-time-components)

```swift
```swift
```swift
```swift
var calendar: Calendar.Identifier?
```
```

The calendar used by the locale.
```
```swift
```swift
```swift
enum Identifier
```
```

An enumeration for the available calendars.
```
```swift
```swift
```swift
var firstDayOfWeek: Locale.Weekday?
```
```

The first day of the week as represented by this locale.
```
```swift
```swift
```swift
enum Weekday
```
```

A type that represents weekdays, used for indicating a locale’s first day of the week.
```
```swift
```swift
```swift
var hourCycle: Locale.HourCycle?
```
```

The hour cycle used by the locale, like one-to-twelve or zero-to-twenty-three.
```
```swift
```swift
```swift
enum HourCycle
```
```

A type that represents the hour cycle used in a locale, like one-to-twelve or zero-to-twenty-three.
```
```swift
```swift
```swift
var timeZone: TimeZone?
```
```

The time zone used by the locale.
```
```

### [Specifiying measurement and counting components](/documentation/Foundation/Locale/Components#Specifiying-measurement-and-counting-components)

```swift
```swift
```swift
```swift
var currency: Locale.Currency?
```
```

The currency used by the locale.
```
```swift
```swift
```swift
struct Currency
```
```

A type that represents the currency system used by a locale, like dollars or euros.
```
```swift
```swift
```swift
var measurementSystem: Locale.MeasurementSystem?
```
```

The measurement system used by the locale, like metric or the US system.
```
```swift
```swift
```swift
struct MeasurementSystem
```
```

A type that represents the measurement system used by a locale, like metric or the US system.
```
```swift
```swift
```swift
var numberingSystem: Locale.NumberingSystem?
```
```

The numbering system used by the locale.
```
```swift
```swift
```swift
struct NumberingSystem
```
```

A type that represents the numbering system used in a locale.
```
```

### [Specifying region components](/documentation/Foundation/Locale/Components#Specifying-region-components)

```swift
```swift
```swift
```swift
var region: Locale.Region?
```
```

The region used by the locale.
```
```swift
```swift
```swift
struct Region
```
```

A type that represents a geographic region, for use in specifying a locale or language.
```
```swift
```swift
```swift
var subdivision: Locale.Subdivision?
```
```

The optional subdivision of the region used by this locale.
```
```swift
```swift
```swift
struct Subdivision
```
```

A type that represents a subdivision of a region, such as a state in the US or a province in Canada.
```
```swift
```swift
```swift
var variant: Locale.Variant?
```
```

An optional variant used by the locale.
```
```swift
```swift
```swift
struct Variant
```
```

A type that represents a locale’s languate variant.
```
```

### [Specifying ordering components](/documentation/Foundation/Locale/Components#Specifying-ordering-components)

```swift
```swift
```swift
```swift
var collation: Locale.Collation?
```
```

The string sort order of the locale.
```
```swift
```swift
```swift
struct Collation
```
```

A type that represents the string sort order used by the locale.
```
```

## [Relationships](/documentation/Foundation/Locale/Components#relationships)

### [Conforms To](/documentation/Foundation/Locale/Components#conforms-to)

*   [`Decodable`](/documentation/Swift/Decodable)
*   [`Encodable`](/documentation/Swift/Encodable)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`Sendable`](/documentation/Swift/Sendable)
*   [`SendableMetatype`](/documentation/Swift/SendableMetatype)

## [See Also](/documentation/Foundation/Locale/Components#see-also)

### [Creating a locale by components](/documentation/Foundation/Locale/Components#Creating-a-locale-by-components)

[`init(components: Locale.Components)`](/documentation/foundation/locale/init\(components:\))

Creates a locale from the given components.

[`init(languageCode: Locale.LanguageCode?, script: Locale.Script?, languageRegion: Locale.Region?)`](/documentation/foundation/locale/init\(languagecode:script:languageregion:\))

Creates a locale with the specified language code, script, and region identifier.

[`init(languageComponents: Locale.Language.Components)`](/documentation/foundation/locale/init\(languagecomponents:\))

Creates a locale from the given language components.

```swift
```swift
```swift
struct Components
```
```

A type that identifies a language by its various components.
```