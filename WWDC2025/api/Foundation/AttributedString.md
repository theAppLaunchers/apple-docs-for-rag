*   [Foundation](/documentation/foundation)
*   AttributedString

Structure

# AttributedString

A value type for a string with associated attributes for portions of its text.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift

```swift
@dynamicMemberLookup
struct AttributedString
```

```
```
```
```
```
```
```

## [Overview](/documentation/Foundation/AttributedString#overview)

Attributed strings are character strings that have attributes for individual characters or ranges of characters. Attributes provide traits like visual styles for display, accessibility for guided access, and hyperlink data for linking between data sources. Attribute keys provide the name and value type of each attribute. System frameworks like Foundation and SwiftUI define common keys, and you can define your own in custom extensions.

### [String Attributes](/documentation/Foundation/AttributedString#String-Attributes)

You can apply an attribute to an entire string, or to a range within the string. The string represents each range with consistent attributes as a _run_.

[`AttributedString`](/documentation/foundation/attributedstring) uses subscripts and dynamic member lookup to simplify working with attributes from your call points. In its most verbose form, you set an attribute by creating an [`AttributeContainer`](/documentation/foundation/attributecontainer) and merging it into an existing attributed string, like this:

```swift
```swift
```swift
```swift
```swift
```swift
var attributedString = AttributedString("This is a string with empty attributes.")
```
```
```swift
```swift
var container = AttributeContainer()
```
```
container[AttributeScopes.AppKitAttributes.ForegroundColorAttribute.self] = .red
attributedString.mergeAttributes(container, mergePolicy: .keepNew)
```
```
```
```

Using the attributed string’s [`subscript(_:)`](/documentation/foundation/attributedstringprotocol/subscript\(_:\)-4thnp) method, you can omit the explicit use of an [`AttributeContainer`](/documentation/foundation/attributecontainer) and just set the attribute by its type:

```

```
attributedString[AttributeScopes.AppKitAttributes.ForegroundColorAttribute.self] = .yellow
```

```

Because an [`AttributedString`](/documentation/foundation/attributedstring) supports dynamic member lookup — as described under [Attributes](https://docs.swift.org/swift-book/ReferenceManual/Attributes.html) in [The Swift Programming Language](https://docs.swift.org/swift-book/) — you can access its subscripts with dot syntax instead. When combined with properties like [`foregroundColor`](/documentation/foundation/attributescopes/appkitattributes/foregroundcolor) that return the attribute key type, this final form offers a natural way to set an attribute that applies to an entire string:

```

```
attributedString.foregroundColor = .green
```

```

This example works because AppKit defines an [`AttributeScope`](/documentation/foundation/attributescope), [`AttributeScopes.AppKitAttributes`](/documentation/foundation/attributescopes/appkitattributes), in which the property [`foregroundColor`](/documentation/foundation/attributescopes/appkitattributes/foregroundcolor) returns the type `AttributeScopes.AppKitAttributes.ForegroundColorAttribute`. Because AppKit’s attribute scope implements [`AttributeDynamicLookup`](/documentation/foundation/attributedynamiclookup), the dot syntax resolves to an equivalent subscript expression, allowing `attributedString.foregroundColor` to replace `attributedString[AttributeScopes.AppKitAttributes.ForegroundColorAttribute.self]`.

You can also set an attribute to apply only to part of an attributed string, by applying the attribute to a range, as seen here:

```swift
```swift
```swift
```swift
```swift
```swift
var attributedString = AttributedString("The first month of your subscription is free.")
```
```
guard let range = attributedString.range(of: "free") else {return}
attributedString[range].foregroundColor = .green
```
```
```
```

You can access portions of the string with unique combinations of attributes by iterating over the string’s `runs` property.

You can define your own custom attributes by creating types that conform to [`AttributedStringKey`](/documentation/foundation/attributedstringkey), and collecting them in an [`AttributeScope`](/documentation/foundation/attributescope). Custom keys should also extend [`AttributeDynamicLookup`](/documentation/foundation/attributedynamiclookup), so callers can use dot-syntax to access the attribute.

### [Creating Attributed Strings with Markdown](/documentation/Foundation/AttributedString#Creating-Attributed-Strings-with-Markdown)

You can create an attributed string by passing a standard [`String`](/documentation/Swift/String) or [`Data`](/documentation/foundation/data) instance that contains Markdown to initializers like [`init(markdown:options:baseURL:)`](/documentation/foundation/attributedstring/init\(markdown:options:baseurl:\)-52n3u). The attributed string creates attributes by parsing the markup in the string.

```swift

```swift
do {
    let thankYouString = try AttributedString(
        markdown:"**Thank you!** Please visit our [website](https://example.com)")
} catch {
    print("Couldn't parse the string. \(error.localizedDescription)")
}
```

```

Localized strings that you load from strings files with initializers like [`init(localized:options:table:bundle:locale:comment:)`](/documentation/foundation/attributedstring/init\(localized:options:table:bundle:locale:comment:\)-8dlnl) can also contain Markdown to add styling. In addition, these localized attributed string initializers can apply the [`replacementIndex`](/documentation/foundation/attributescopes/foundationattributes/replacementindex) attribute, which allows you to determine the range of replacement strings, whose order may vary between languages.

By declaring new attributes that conform to [`MarkdownDecodableAttributedStringKey`](/documentation/foundation/markdowndecodableattributedstringkey), you can add attributes that you invoke by using Apple’s Markdown extension syntax: `^[text](name:value, name:value, …)`. See the sample code project doc:building-a-localized-food-ordering-app for an example of creating custom attributes and using them with Markdown.

Localized attributed strings can also use the extension syntax to indicate parts of the string where the system can apply automatic grammar agreement. See the initializers that take a `localized:` parameter for examples of this extension syntax, as used with automatic grammar agreement.

### [Attribute Scopes](/documentation/Foundation/AttributedString#Attribute-Scopes)

The [`AttributedString`](/documentation/foundation/attributedstring) API defines keys for common uses, such as text styling, semantically marking up formattable types like dates and numbers, and hyperlinking. You can find these in the [`AttributeScopes`](/documentation/foundation/attributescopes) enumeration, which contains attributes for AppKit, Foundation, SwiftUI, and UIKit.

You can define your own attributes by implementing [`AttributedStringKey`](/documentation/foundation/attributedstringkey), and reference them by name by collecting them in an [`AttributeScope`](/documentation/foundation/attributescope).

## [Topics](/documentation/Foundation/AttributedString#topics)

### [Creating an Attributed String](/documentation/Foundation/AttributedString#Creating-an-Attributed-String)

[`init()`](/documentation/foundation/attributedstring/init\(\))

Creates an empty attributed string.

[`init(AttributedSubstring)`](/documentation/foundation/attributedstring/init\(_:\)-8tnoq)

Creates an attributed string from an attributed substring.

[`init(String, attributes: AttributeContainer)`](/documentation/foundation/attributedstring/init\(_:attributes:\)-2a45h)

Creates an attributed string from a string and an attribute container.

[`init(Substring, attributes: AttributeContainer)`](/documentation/foundation/attributedstring/init\(_:attributes:\)-8jqhp)

Creates an attributed string from a substring and an attribute container.

[`init<S>(S, attributes: AttributeContainer)`](/documentation/foundation/attributedstring/init\(_:attributes:\)-8l0iq)

Creates an attributed string from a character sequence and an attribute container.

```swift
```swift
```swift
struct AttributeContainer
```
```

A container for attribute keys and values.
```

### [Creating a Localized Attributed String](/documentation/Foundation/AttributedString#Creating-a-Localized-Attributed-String)

[`init(localized: String.LocalizationValue, options: AttributedString.FormattingOptions, table: String?, bundle: Bundle?, locale: Locale?, comment: StaticString?)`](/documentation/foundation/attributedstring/init\(localized:options:table:bundle:locale:comment:\)-8dlnl)

Creates an attributed string by looking up a localized string from the app’s bundle.

[`init<S>(localized: String.LocalizationValue, options: AttributedString.FormattingOptions, table: String?, bundle: Bundle?, locale: Locale?, comment: StaticString?, including: S.Type)`](/documentation/foundation/attributedstring/init\(localized:options:table:bundle:locale:comment:including:\)-8uknv)

Creates an attributed string by looking up a localized string from the app’s bundle, including an attribute scope.

[`init<S>(localized: String.LocalizationValue, options: AttributedString.FormattingOptions, table: String?, bundle: Bundle?, locale: Locale?, comment: StaticString?, including: KeyPath<AttributeScopes, S.Type>)`](/documentation/foundation/attributedstring/init\(localized:options:table:bundle:locale:comment:including:\)-5jzpg)

Creates an attributed string by looking up a localized string from the app’s bundle, including an attribute scope that a key path identifies.

```swift
```swift
```swift
struct LocalizationValue
```
```

A reference to a localizable string, with optional string interpolation.
```
```swift
```swift
```swift
struct FormattingOptions
```
```

Options that affect the handling of attributes.
```

[`init(localized: LocalizedStringResource)`](/documentation/foundation/attributedstring/init\(localized:\))

Creates a localized attributed string from a localized string resource.

[`init<S>(localized: LocalizedStringResource, including: S.Type)`](/documentation/foundation/attributedstring/init\(localized:including:\)-2xebo)

Creates a localized attributed string from a localized string resource, including an attribute scope.

[`init<S>(localized: LocalizedStringResource, including: KeyPath<AttributeScopes, S.Type>)`](/documentation/foundation/attributedstring/init\(localized:including:\)-15xc5)

Creates a localized attributed string from a localized string resource, including an attribute scope that a key path identifies.

```swift
```swift
```swift
struct LocalizedStringResource
```
```

A reference to a localizable string, accessible from another process.
```

### [Creating a Localized Attributed String with a Default Value](/documentation/Foundation/AttributedString#Creating-a-Localized-Attributed-String-with-a-Default-Value)

[`init(localized: StaticString, defaultValue: String.LocalizationValue, options: AttributedString.FormattingOptions, table: String?, bundle: Bundle?, locale: Locale?, comment: StaticString?)`](/documentation/foundation/attributedstring/init\(localized:defaultvalue:options:table:bundle:locale:comment:\)-4n8e2)

Creates an attributed string by looking up a localized string from the app’s bundle, using a default value if necessary.

[`init<S>(localized: StaticString, defaultValue: String.LocalizationValue, options: AttributedString.FormattingOptions, table: String?, bundle: Bundle?, locale: Locale?, comment: StaticString?, including: S.Type)`](/documentation/foundation/attributedstring/init\(localized:defaultvalue:options:table:bundle:locale:comment:including:\)-2elmp)

Creates an attributed string by looking up a localized string from the app’s bundle, including an attribute scope, using a default value if necessary.

[`init<S>(localized: StaticString, defaultValue: String.LocalizationValue, options: AttributedString.FormattingOptions, table: String?, bundle: Bundle?, locale: Locale?, comment: StaticString?, including: KeyPath<AttributeScopes, S.Type>)`](/documentation/foundation/attributedstring/init\(localized:defaultvalue:options:table:bundle:locale:comment:including:\)-9gjtg)

Creates an attributed string by looking up a localized string from the app’s bundle, including an attribute scope that a key path identifies, using a default value if necessary.

### [Creating an Attributed String from Markdown](/documentation/Foundation/AttributedString#Creating-an-Attributed-String-from-Markdown)

Use Markdown syntax to initialize an attributed string with text and attributes.

[

API Reference

Instantiating Attributed Strings with Markdown Syntax](/documentation/foundation/instantiating-attributed-strings-with-markdown-syntax)

Use a Markdown-syntax string to iniitalize an attributed string with standard or custom attributes.

### [Creating an Attributed String from a Reference Type](/documentation/Foundation/AttributedString#Creating-an-Attributed-String-from-a-Reference-Type)

[`init<S>(NSAttributedString, including: S.Type) throws`](/documentation/foundation/attributedstring/init\(_:including:\)-9no47)

Creates a value-type attributed string from a reference type, including an attribute scope.

[`init<S>(NSAttributedString, including: KeyPath<AttributeScopes, S.Type>) throws`](/documentation/foundation/attributedstring/init\(_:including:\)-puv0)

Creates a value-type attributed string from a reference type, including an attribute scope that a key path identifies.

[`init(NSAttributedString)`](/documentation/foundation/attributedstring/init\(_:\)-1fru0)

Creates a value-type attributed string from a reference type.

### [Creating a Duplicate Attributed String](/documentation/Foundation/AttributedString#Creating-a-Duplicate-Attributed-String)

[`init<S, T>(T, including: S.Type)`](/documentation/foundation/attributedstring/init\(_:including:\)-6u3ho)

Creates an attributed string from another attributed string, including an attribute scope.

[`init<S, T>(T, including: KeyPath<AttributeScopes, S.Type>)`](/documentation/foundation/attributedstring/init\(_:including:\)-9ejyj)

Creates an attributed string from another attributed string, including an attribute scope that a key path identifies.

### [Applying and Modifying Attributes](/documentation/Foundation/AttributedString#Applying-and-Modifying-Attributes)

```swift
```swift
```swift
```swift
enum AttributeMergePolicy
```
```

An enumeration of behaviors to apply when merging attributes.
```
```swift
```swift
```swift
protocol AttributedStringAttributeMutation
```
```

A protocol that defines in-place mutations for attributes in an attributed string.
```
```

### [Using Defined Attributes](/documentation/Foundation/AttributedString#Using-Defined-Attributes)

```swift
```swift
```swift
```swift
enum AttributeScopes
```
```

Collections of attributes that system frameworks define.
```
```swift
```swift
```swift
enum AttributeDynamicLookup
```
```

A type to support dynamic member lookup of attributes and containers.
```
```swift
```swift
```swift
struct ScopedAttributeContainer
```
```

An attribute container that allows dynamic member lookup of its contents within the specified attribute scope.
```
```

### [Accessing Indices](/documentation/Foundation/AttributedString#Accessing-Indices)

[

API Reference

Accessing Indicies Within an Attributed String](/documentation/foundation/accessing-indicies-within-an-attributed-string)

Access a position within an attributed string, offset from the beginning, or before or after another known position.

### [Accessing Views into the Attributed String](/documentation/Foundation/AttributedString#Accessing-Views-into-the-Attributed-String)

```swift
```swift
```swift
```swift
struct CharacterView
```
```

A view into the underlying storage of the attributed string, as Unicode characters.
```
```swift
```swift
```swift
struct UnicodeScalarView
```
```

A view into the underlying storage of the attributed string, as Unicode scalars.
```
```swift
```swift
```swift
struct Runs
```
```

An iterable view into segments of the attributed string, each of which indicates where a run of identical attributes begins or ends.
```
```

### [Modifying an Attributed String](/documentation/Foundation/AttributedString#Modifying-an-Attributed-String)

```swift
```swift
```swift
```swift
func insert(some AttributedStringProtocol, at: AttributedString.Index)
```
```

Inserts the specified string at a specific index in the attributed string.
```
```swift
```swift
```swift
struct Index
```
```

A type that represents the position of a character or code unit within an attributed string.
```
```swift
```swift
```swift
func removeSubrange(some RangeExpression<AttributedString.Index>)
```
```

Removes a range of characters from the attributed string.
```
```swift
```swift
```swift
func replaceSubrange(some RangeExpression<AttributedString.Index>, with: some AttributedStringProtocol)
```
```

Replaces the contents in a range of the attributed string.
```
```

### [Transforming Attributes](/documentation/Foundation/AttributedString#Transforming-Attributes)

```swift
```swift
```swift
```swift
func transformingAttributes<K>(K.Type, (inout AttributedString.SingleAttributeTransformer<K>) -> Void) -> AttributedString
```
```

Returns an attributed string by calling a closure that transforms one attribute of a source attributed string.
```
```swift
```swift
```swift
func transformingAttributes<K>(KeyPath<AttributeDynamicLookup, K>, (inout AttributedString.SingleAttributeTransformer<K>) -> Void) -> AttributedString
```
```

Returns an attributed string by calling a closure that transforms one attribute, which a key path identifies, of a source attributed string.
```
```swift
```swift
```swift
func transformingAttributes<K1, K2>(K1.Type, K2.Type, (inout AttributedString.SingleAttributeTransformer<K1>, inout AttributedString.SingleAttributeTransformer<K2>) -> Void) -> AttributedString
```
```

Returns an attributed string by calling a closure that transforms two attributes of a source attributed string.
```
```swift
```swift
```swift
func transformingAttributes<K1, K2>(KeyPath<AttributeDynamicLookup, K1>, KeyPath<AttributeDynamicLookup, K2>, (inout AttributedString.SingleAttributeTransformer<K1>, inout AttributedString.SingleAttributeTransformer<K2>) -> Void) -> AttributedString
```
```

Returns an attributed string created by calling a closure that transforms two attributes, which key paths identify, of a source attributed string.
```
```swift
```swift
```swift
func transformingAttributes<K1, K2, K3>(K1.Type, K2.Type, K3.Type, (inout AttributedString.SingleAttributeTransformer<K1>, inout AttributedString.SingleAttributeTransformer<K2>, inout AttributedString.SingleAttributeTransformer<K3>) -> Void) -> AttributedString
```
```

Returns an attributed string by calling a closure that transforms three attributes of a source attributed string.
```
```swift
```swift
```swift
func transformingAttributes<K1, K2, K3>(KeyPath<AttributeDynamicLookup, K1>, KeyPath<AttributeDynamicLookup, K2>, KeyPath<AttributeDynamicLookup, K3>, (inout AttributedString.SingleAttributeTransformer<K1>, inout AttributedString.SingleAttributeTransformer<K2>, inout AttributedString.SingleAttributeTransformer<K3>) -> Void) -> AttributedString
```
```

Returns an attributed string by calling a closure that transforms three attributes, which key paths identify, of a source attributed string.
```
```swift
```swift
```swift
func transformingAttributes<K1, K2, K3, K4>(K1.Type, K2.Type, K3.Type, K4.Type, (inout AttributedString.SingleAttributeTransformer<K1>, inout AttributedString.SingleAttributeTransformer<K2>, inout AttributedString.SingleAttributeTransformer<K3>, inout AttributedString.SingleAttributeTransformer<K4>) -> Void) -> AttributedString
```
```

Returns an attributed string by calling a closure that transforms four attributes of a source attributed string.
```
```swift
```swift
```swift
func transformingAttributes<K1, K2, K3, K4>(KeyPath<AttributeDynamicLookup, K1>, KeyPath<AttributeDynamicLookup, K2>, KeyPath<AttributeDynamicLookup, K3>, KeyPath<AttributeDynamicLookup, K4>, (inout AttributedString.SingleAttributeTransformer<K1>, inout AttributedString.SingleAttributeTransformer<K2>, inout AttributedString.SingleAttributeTransformer<K3>, inout AttributedString.SingleAttributeTransformer<K4>) -> Void) -> AttributedString
```
```

Returns an attributed string created by calling a closure that transforms four attributes, which key paths identify, of a source attributed string.
```
```swift
```swift
```swift
func transformingAttributes<K1, K2, K3, K4, K5>(K1.Type, K2.Type, K3.Type, K4.Type, K5.Type, (inout AttributedString.SingleAttributeTransformer<K1>, inout AttributedString.SingleAttributeTransformer<K2>, inout AttributedString.SingleAttributeTransformer<K3>, inout AttributedString.SingleAttributeTransformer<K4>, inout AttributedString.SingleAttributeTransformer<K5>) -> Void) -> AttributedString
```
```

Returns an attributed string created by calling a closure that transforms five attributes of a source attributed string.
```
```swift
```swift
```swift
func transformingAttributes<K1, K2, K3, K4, K5>(KeyPath<AttributeDynamicLookup, K1>, KeyPath<AttributeDynamicLookup, K2>, KeyPath<AttributeDynamicLookup, K3>, KeyPath<AttributeDynamicLookup, K4>, KeyPath<AttributeDynamicLookup, K5>, (inout AttributedString.SingleAttributeTransformer<K1>, inout AttributedString.SingleAttributeTransformer<K2>, inout AttributedString.SingleAttributeTransformer<K3>, inout AttributedString.SingleAttributeTransformer<K4>, inout AttributedString.SingleAttributeTransformer<K5>) -> Void) -> AttributedString
```
```

Returns an attributed string created by calling a closure that transforms five attributes, which key paths identify, of a source attributed string.
```
```swift
```swift
```swift
struct SingleAttributeTransformer
```
```

A type that transforms an attribute by altering its range or value, or by replacing it entirely.
```
```

### [Accessing Whole-String Attributes](/documentation/Foundation/AttributedString#Accessing-Whole-String-Attributes)

```swift
```swift
```swift
```swift
enum AttributeDynamicLookup
```
```

A type to support dynamic member lookup of attributes and containers.
```
```swift
```swift
```swift
struct ScopedAttributeContainer
```
```

An attribute container that allows dynamic member lookup of its contents within the specified attribute scope.
```
```

### [Combining Attributed Strings](/documentation/Foundation/AttributedString#Combining-Attributed-Strings)

```swift
```swift
```swift
```swift
func append(some AttributedStringProtocol)
```
```

Appends a string to the attributed string.
```

[`static func + (AttributedString, AttributedString) -> AttributedString`](/documentation/foundation/attributedstring/+\(_:_:\)-8sbsq)

Concatenates two attributed strings.

[`static func + (AttributedString, some AttributedStringProtocol) -> AttributedString`](/documentation/foundation/attributedstring/+\(_:_:\)-drfc)

Concatenates two attributed strings or substrings.

[`static func += (inout AttributedString, AttributedString)`](/documentation/foundation/attributedstring/+=\(_:_:\)-4dk88)

Appends an attributed string to another attributed string.

[`static func += (inout AttributedString, some AttributedStringProtocol)`](/documentation/foundation/attributedstring/+=\(_:_:\)-6yimu)

Appends an attributed string or substring to another attributed string.
```

### [Performing Automatic Grammar Agreement](/documentation/Foundation/AttributedString#Performing-Automatic-Grammar-Agreement)

```swift
```swift
```swift
```swift
func inflected() -> AttributedString
```
```

Applies automatic grammar agreement inflection rules to the attributed string and returns the result.
```
```

### [Performing String Interpolation](/documentation/Foundation/AttributedString#Performing-String-Interpolation)

```swift
```swift
```swift
```swift
struct InterpolationOptions
```
```

Options that affect the behavior of string interpolation on the attributed string.
```
```

### [Encoding and Decoding](/documentation/Foundation/AttributedString#Encoding-and-Decoding)

```swift
```swift
```swift
```swift
struct AttributeScopeCodableConfiguration
```
```

A configuration type for encoding and decoding attributed strings.
```

[

API Reference

Encoding and Decoding Attributed String Keys](/documentation/foundation/encoding-and-decoding-attributed-string-keys)

Protocols adopted by attribute keys to encode or decode data.
```

### [Structures](/documentation/Foundation/AttributedString#Structures)

```swift
```swift
```swift
```swift
struct AdaptiveImageGlyph
```
```
```
```swift
```swift
```swift
struct AttributeInvalidationCondition
```
```
```
```swift
```swift
```swift
struct LineHeight
```
```

The line height definition of a paragraph.

Beta
```
```swift
```swift
```swift
struct LocalizationOptions
```
```

Configuration options for the localization of text.
```
```swift
```swift
```swift
struct MarkdownSourcePosition
```
```

The position of attributed string text in its original Markdown source string.
```
```swift
```swift
```swift
struct UTF16View
```
```
```
```swift
```swift
```swift
struct UTF8View
```
```
```
```

### [Initializers](/documentation/Foundation/AttributedString#Initializers)

[`init(DiscontiguousAttributedSubstring)`](/documentation/foundation/attributedstring/init\(_:\)-83wi)

[`init(localized: StaticString, defaultValue: String.LocalizationValue, options: AttributedString.LocalizationOptions, table: String?, bundle: Bundle?, locale: Locale?, comment: StaticString?)`](/documentation/foundation/attributedstring/init\(localized:defaultvalue:options:table:bundle:locale:comment:\)-2nmk8)

[`init<S>(localized: StaticString, defaultValue: String.LocalizationValue, options: AttributedString.LocalizationOptions, table: String?, bundle: Bundle?, locale: Locale?, comment: StaticString?, including: S.Type)`](/documentation/foundation/attributedstring/init\(localized:defaultvalue:options:table:bundle:locale:comment:including:\)-6qaoe)

[`init<S>(localized: StaticString, defaultValue: String.LocalizationValue, options: AttributedString.LocalizationOptions, table: String?, bundle: Bundle?, locale: Locale?, comment: StaticString?, including: KeyPath<AttributeScopes, S.Type>)`](/documentation/foundation/attributedstring/init\(localized:defaultvalue:options:table:bundle:locale:comment:including:\)-iisj)

[`init(localized: LocalizedStringResource, options: AttributedString.LocalizationOptions)`](/documentation/foundation/attributedstring/init\(localized:options:\))

[`init<S>(localized: LocalizedStringResource, options: AttributedString.LocalizationOptions, including: S.Type)`](/documentation/foundation/attributedstring/init\(localized:options:including:\)-3dycp)

[`init<S>(localized: LocalizedStringResource, options: AttributedString.LocalizationOptions, including: KeyPath<AttributeScopes, S.Type>)`](/documentation/foundation/attributedstring/init\(localized:options:including:\)-4cbfv)

[`init(localized: String.LocalizationValue, options: AttributedString.LocalizationOptions, table: String?, bundle: Bundle?, locale: Locale?, comment: StaticString?)`](/documentation/foundation/attributedstring/init\(localized:options:table:bundle:locale:comment:\)-1w4s)

[`init<S>(localized: String.LocalizationValue, options: AttributedString.LocalizationOptions, table: String?, bundle: Bundle?, locale: Locale?, comment: StaticString?, including: KeyPath<AttributeScopes, S.Type>)`](/documentation/foundation/attributedstring/init\(localized:options:table:bundle:locale:comment:including:\)-3zy6h)

[`init<S>(localized: String.LocalizationValue, options: AttributedString.LocalizationOptions, table: String?, bundle: Bundle?, locale: Locale?, comment: StaticString?, including: S.Type)`](/documentation/foundation/attributedstring/init\(localized:options:table:bundle:locale:comment:including:\)-8ao6x)

[`init(transferable: AttributedTextFormatting.Transferable, in: EnvironmentValues) throws`](/documentation/foundation/attributedstring/init\(transferable:in:\))

Extract an attributed string from SwiftUI’s transferable representation in a certain environment.

Beta

### [Instance Methods](/documentation/Foundation/AttributedString#Instance-Methods)

```swift
```swift
```swift
```swift
func inflected(locale: Locale, userTermOfAddress: TermOfAddress?, inflectionConcepts: [InflectionConcept]) -> AttributedString
```
```
```
```swift
```swift
```swift
func rangeOfAudioTimeRangeAttributes(intersecting: CMTimeRange) -> Range<AttributedString.Index>?
```
```

Returns the range of indices of the receiver that are part of given time range.

Beta
```
```swift
```swift
```swift
func removeSubranges(RangeSet<AttributedString.Index>)
```
```
```
```swift
```swift
```swift
func replaceSelection(inout AttributedTextSelection, with: some AttributedStringProtocol)
```
```

Replace the selection with new attributed content.

Beta
```
```swift
```swift
```swift
func replaceSelection(inout AttributedTextSelection, withCharacters: some Collection<Character>)
```
```

Replace the selection with new content, attributed with the typing attributes.

Beta
```
```swift
```swift
```swift
func transform<E>(updating: inout Range<AttributedString.Index>, body: (inout AttributedString) throws(E) -> Void) throws(E)
```
```

Tracks the location of the provided range throughout the mutation closure, updating the provided range to one that represents the same effective locations after the mutation. If updating the provided range is not possible (tracking failed) then this function will fatal error. Use the Optional-returning variants to provide custom fallback behavior.
```
```swift
```swift
```swift
func transform<E>(updating: inout [Range<AttributedString.Index>], body: (inout AttributedString) throws(E) -> Void) throws(E)
```
```

Tracks the location of the provided ranges throughout the mutation closure, updating them to new ranges that represent the same effective locations after the mutation. If updating the provided ranges is not possible (tracking failed) then this function will fatal error. Use the Optional-returning variants to provide custom fallback behavior.
```
```swift
```swift
```swift
func transform<E>(updating: Range<AttributedString.Index>, body: (inout AttributedString) throws(E) -> Void) throws(E) -> Range<AttributedString.Index>?
```
```

Tracks the location of the provided range throughout the mutation closure, returning a new, updated range that represents the same effective locations after the mutation
```
```swift
```swift
```swift
func transform<E>(updating: [Range<AttributedString.Index>], body: (inout AttributedString) throws(E) -> Void) throws(E) -> [Range<AttributedString.Index>]?
```
```

Tracks the location of the provided ranges throughout the mutation closure, returning a new, updated range that represents the same effective locations after the mutation
```
```swift
```swift
```swift
func transform<E>(updating: inout AttributedTextSelection, body: (inout AttributedString) throws(E) -> Void) throws(E)
```
```

Tracks the location of the selection throughout the mutation closure, updating the selection so it represents the same effective locations after the mutation.

Beta
```
```swift
```swift
```swift
func transformAttributes<E>(in: inout AttributedTextSelection, body: (inout AttributeContainer) throws(E) -> Void) throws(E)
```
```

Apply a change to the attributes in the entire selection.

Beta
```
```

### [Subscripts](/documentation/Foundation/AttributedString#Subscripts)

[`subscript(AttributedTextSelection) -> DiscontiguousAttributedSubstring`](/documentation/foundation/attributedstring/subscript\(_:\)-2yypq)

Obtain the discontiguous substring of a selection.

Beta

[`subscript(RangeSet<AttributedString.Index>) -> DiscontiguousAttributedSubstring`](/documentation/foundation/attributedstring/subscript\(_:\)-ftoi)

### [Type Aliases](/documentation/Foundation/AttributedString#Type-Aliases)

```swift
```swift
```swift
```swift
typealias Specification
```
```
```
```swift
```swift
```swift
typealias UnwrappedType
```
```
```
```swift
```swift
```swift
typealias ValueType
```
```
```
```

### [Type Properties](/documentation/Foundation/AttributedString#Type-Properties)

[`static var defaultResolverSpecification: some ResolverSpecification`](/documentation/foundation/attributedstring/defaultresolverspecification)

### [Enumerations](/documentation/Foundation/AttributedString#Enumerations)

```swift
```swift
```swift
```swift
enum AttributeRunBoundaries
```
```
```
```swift
```swift
```swift
enum TextAlignment
```
```

The explicit alignment of text within its container.

Beta
```
```swift
```swift
```swift
enum WritingDirection
```
```

The writing direction of a piece of text.
```
```

### [Default Implementations](/documentation/Foundation/AttributedString#Default-Implementations)

[

API Reference

Transferable Implementations](/documentation/foundation/attributedstring/transferable-implementations)

## [Relationships](/documentation/Foundation/AttributedString#relationships)

### [Conforms To](/documentation/Foundation/AttributedString#conforms-to)

*   [`AttributedStringAttributeMutation`](/documentation/foundation/attributedstringattributemutation)
*   [`AttributedStringProtocol`](/documentation/foundation/attributedstringprotocol)
*   [`Copyable`](/documentation/Swift/Copyable)
*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Decodable`](/documentation/Swift/Decodable)
*   [`DecodableWithConfiguration`](/documentation/foundation/decodablewithconfiguration)
*   [`Encodable`](/documentation/Swift/Encodable)
*   [`EncodableWithConfiguration`](/documentation/foundation/encodablewithconfiguration)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`ExpressibleByExtendedGraphemeClusterLiteral`](/documentation/Swift/ExpressibleByExtendedGraphemeClusterLiteral)
*   [`ExpressibleByStringLiteral`](/documentation/Swift/ExpressibleByStringLiteral)
*   [`ExpressibleByUnicodeScalarLiteral`](/documentation/Swift/ExpressibleByUnicodeScalarLiteral)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`Sendable`](/documentation/Swift/Sendable)
*   [`SendableMetatype`](/documentation/Swift/SendableMetatype)
*   [`Transferable`](/documentation/CoreTransferable/Transferable)

## [See Also](/documentation/Foundation/AttributedString#see-also)

### [Strings with Metadata](/documentation/Foundation/AttributedString#Strings-with-Metadata)

```swift
```swift
```swift
```swift
struct AttributedSubstring
```
```

A portion of an attributed string.
```

[

API Reference

Attributed String Supporting Types](/documentation/foundation/attributed-string-supporting-types)

Types that the attributed string, attributed substring, and helper types extend or conform to, for sharing common functionality.

```swift
```swift
```swift
class NSAttributedString
```
```

A string of text that manages data, layout, and stylistic information for ranges of characters to support rendering.
```
```swift
```swift
```swift
class NSMutableAttributedString
```
```

A mutable string with associated attributes (such as visual style, hyperlinks, or accessibility data) for portions of its text.
```
```