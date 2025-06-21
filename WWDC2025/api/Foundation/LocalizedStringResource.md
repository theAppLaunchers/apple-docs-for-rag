*   [Foundation](/documentation/foundation)
*   LocalizedStringResource

Structure

# LocalizedStringResource

A reference to a localizable string, accessible from another process.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
struct LocalizedStringResource
```
```
```
```
```
```
```
```

## [Overview](/documentation/Foundation/LocalizedStringResource#overview)

Use [`LocalizedStringResource`](/documentation/foundation/localizedstringresource) to provide localizable strings with lookups you defer to a later time.

When you create a localized string or a localized attributed string with an initializer that takes [`String.LocalizationValue`](/documentation/Swift/String/LocalizationValue), those initializers lookup the localized string immediately. If you want to perform the lookup at a later time, use this [`LocalizedStringResource`](/documentation/foundation/localizedstringresource) type to refer to the localizable strings. Then, when you need to perform localization, create a [`String`](/documentation/Swift/String) or [`AttributedString`](/documentation/foundation/attributedstring) from an initializer that takes a [`LocalizedStringResource`](/documentation/foundation/localizedstringresource) parameter, such as:

*   [`String`](/documentation/Swift/String): [`init(localized:)`](/documentation/Swift/String/init\(localized:\)) or [`init(localized:options:)`](/documentation/Swift/String/init\(localized:options:\)).
    
*   [`AttributedString`](/documentation/foundation/attributedstring): [`init(localized:)`](/documentation/foundation/attributedstring/init\(localized:\)), [`init(localized:including:)`](/documentation/foundation/attributedstring/init\(localized:including:\)-2xebo), or [`init(localized:including:)`](/documentation/foundation/attributedstring/init\(localized:including:\)-15xc5).
    

This approach allows you to provide localizable strings to an entirely separate process, which may use a different locale. For example, consider an app with a data model type called `UserAction` that uses [`LocalizedStringResource`](/documentation/foundation/localizedstringresource) rather than strings for its `title` and `description` properties.

```swift

```swift
public protocol UserAction {
    static var title: LocalizedStringResource { get }
    static var description: LocalizedStringResource { get }
}
```

```

This app (or one of its embedded frameworks) then uses these [`LocalizedStringResource`](/documentation/foundation/localizedstringresource) members to defer looking up localized strings. Typically, this happens when calling out to another process over XPC.

```swift

```swift
public func perform(action: UserAction) {
    ...
    // Send text to another process via XPC or similar.
    performActionOutOfProcess(title: action.title, description: action.description)
}
```

```

Then, when the other process receives the call, it can alter the [`locale`](/documentation/foundation/localizedstringresource/locale) in the [`LocalizedStringResource`](/documentation/foundation/localizedstringresource), prior to resolving the localized strings.

```swift
```swift
```swift
```swift
```swift
```swift
func performActionOutOfProcess(title: LocalizedStringResource,
```
```
                               description: LocalizedStringResource) {
    // Set resource locales to match the current locale
    // of the separate process.
    var fixedTitle = title
    fixedTitle.locale = .current
    var fixedDescription = description
    fixedDescription.locale = .current
    
    // Look up localized strings.
    let titleString = String(localized: fixedTitle)
    let descriptionString = String(localized: fixedDescription)
        
    // Use a correctly localized title/description.
}
```
```
```
```

The [App Intents](/documentation/AppIntents) framework uses [`LocalizedStringResource`](/documentation/foundation/localizedstringresource) to perform a late resolution of localized strings. This allows the Siri UI to potentially use different localization preferences than the app providing the intent.

## [Topics](/documentation/Foundation/LocalizedStringResource#topics)

### [Accessing resource properties](/documentation/Foundation/LocalizedStringResource#Accessing-resource-properties)

```swift
```swift
```swift
```swift
let key: String
```
```

The key to use to look up a localized string.
```
```swift
```swift
```swift
let defaultValue: String.LocalizationValue
```
```

The resource’s default value.
```
```swift
```swift
```swift
let table: String?
```
```

The name of the table containing the key-value pairs.
```
```swift
```swift
```swift
var bundle: LocalizedStringResource.BundleDescription
```
```

The bundle containing the table’s strings file.
```
```swift
```swift
```swift
enum BundleDescription
```
```

The location of a bundle to use for looking up localized strings, such as the main bundle, or a bundle at a specific file URL.
```
```swift
```swift
```swift
var locale: Locale
```
```

The locale to use to look up the localized string from the string resource.
```
```

### [Initializers](/documentation/Foundation/LocalizedStringResource#Initializers)

[`init(StaticString, defaultValue: String.LocalizationValue, table: String?, locale: Locale, bundle: LocalizedStringResource.BundleDescription, comment: StaticString?)`](/documentation/foundation/localizedstringresource/init\(_:defaultvalue:table:locale:bundle:comment:\)-1apqa)

[`init(StaticString, defaultValue: String.LocalizationValue, table: String?, locale: Locale, bundle: Bundle, comment: StaticString?)`](/documentation/foundation/localizedstringresource/init\(_:defaultvalue:table:locale:bundle:comment:\)-8jyvr)

[`init(String.LocalizationValue, table: String?, locale: Locale, bundle: LocalizedStringResource.BundleDescription, comment: StaticString?)`](/documentation/foundation/localizedstringresource/init\(_:table:locale:bundle:comment:\)-69k32)

[`init(String.LocalizationValue, table: String?, locale: Locale, bundle: Bundle, comment: StaticString?)`](/documentation/foundation/localizedstringresource/init\(_:table:locale:bundle:comment:\)-8o153)

## [Relationships](/documentation/Foundation/LocalizedStringResource#relationships)

### [Conforms To](/documentation/Foundation/LocalizedStringResource#conforms-to)

*   [`CustomLocalizedStringResourceConvertible`](/documentation/foundation/customlocalizedstringresourceconvertible)
*   [`Decodable`](/documentation/Swift/Decodable)
*   [`Encodable`](/documentation/Swift/Encodable)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`ExpressibleByExtendedGraphemeClusterLiteral`](/documentation/Swift/ExpressibleByExtendedGraphemeClusterLiteral)
*   [`ExpressibleByStringInterpolation`](/documentation/Swift/ExpressibleByStringInterpolation)
*   [`ExpressibleByStringLiteral`](/documentation/Swift/ExpressibleByStringLiteral)
*   [`ExpressibleByUnicodeScalarLiteral`](/documentation/Swift/ExpressibleByUnicodeScalarLiteral)
*   [`Sendable`](/documentation/Swift/Sendable)
*   [`SendableMetatype`](/documentation/Swift/SendableMetatype)

## [See Also](/documentation/Foundation/LocalizedStringResource#see-also)

### [Localization](/documentation/Foundation/LocalizedStringResource#Localization)

```swift
```swift
```swift
```swift
struct Locale
```
```

Information about linguistic, cultural, and technological conventions for use in formatting data for presentation.
```
```swift
```swift
```swift
class NSOrthography
```
```

A description of the linguistic content of natural language text, typically used for spelling and grammar checking.
```
```swift
```swift
```swift
func NSLocalizedString(String, tableName: String?, bundle: Bundle, value: String, comment: String) -> String
```
```

Returns a localized string from a table that Xcode generates for you when exporting localizations.
```
```swift
```swift
```swift
protocol CustomLocalizedStringResourceConvertible
```
```

A type that provides an out-of-process localizable description.
```
```swift
```swift
```swift
struct URLResource
```
```

A resource located at a particular file URL within a bundle.
```
```