*   [Foundation](/documentation/foundation)
*   Morphology

Structure

# Morphology

A description of the grammatical properties of a string.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
struct Morphology
```
```
```
```
```
```
```
```

## [Overview](/documentation/Foundation/Morphology#overview)

Use a morphology with an [`InflectionRule`](/documentation/foundation/inflectionrule) to specify how to interpret a specific word when inflecting an [`AttributedString`](/documentation/foundation/attributedstring). This affects grammatical agreement with traits like number and gender, as well as declaring the word’s part of speech.

The [`Morphology`](/documentation/foundation/morphology) type’s design is language-independent; the concepts it can specify encompass the spectrum of what languages can do. Even for languages that don’t have one or more of those properties benefit the system as hints to make appropriate choices even when an exact inflection isn’t possible. Examples of properties absent from languages include Spanish’s lack of a grammatical gender of neuter, or the nonexistence of a paucal (plural few) pronoun in English.

## [Topics](/documentation/Foundation/Morphology#topics)

### [Creating a Morphology Instance](/documentation/Foundation/Morphology#Creating-a-Morphology-Instance)

[`init()`](/documentation/foundation/morphology/init\(\))

Creates an empty morphology instance.

### [Accessing the User’s Morphology](/documentation/Foundation/Morphology#Accessing-the-Users-Morphology)

[`static let user: Morphology`](/documentation/foundation/morphology/user)

The addressing preferences of the current user.

### [Accessing Grammatical Properties](/documentation/Foundation/Morphology#Accessing-Grammatical-Properties)

```swift
```swift
```swift
```swift
var isUnspecified: Bool
```
```

A Boolean value that indicates whether this instance specifies no particular grammar.
```
```swift
```swift
```swift
var grammaticalGender: Morphology.GrammaticalGender?
```
```

The grammatical gender used for inflecting strings with this morphology.
```
```swift
```swift
```swift
enum GrammaticalGender
```
```

A representation of grammatical gender, used for inflecting strings.
```
```swift
```swift
```swift
var number: Morphology.GrammaticalNumber?
```
```

The grammatical number used for inflecting strings with this morphology.
```
```swift
```swift
```swift
enum GrammaticalNumber
```
```

A representation of grammatical number, used for inflecting strings.
```
```swift
```swift
```swift
var partOfSpeech: Morphology.PartOfSpeech?
```
```

The grammatical part of speech used for inflecting strings with this morphology.
```
```swift
```swift
```swift
enum PartOfSpeech
```
```

A representation of grammatical parts of speech, used for inflecting strings.
```
```

### [Accessing Per-Language Features](/documentation/Foundation/Morphology#Accessing-Per-Language-Features)

```swift
```swift
```swift
```swift
func setCustomPronoun(Morphology.CustomPronoun?, forLanguage: String) throws
```
```

Sets a custom pronoun behavior for this morphology to apply to the given language.

Deprecated
```
```swift
```swift
```swift
func customPronoun(forLanguage: String) -> Morphology.CustomPronoun?
```
```

Returns any custom pronoun behavior this morphology applies to the given language.

Deprecated
```
```swift
```swift
```swift
struct CustomPronoun
```
```

A custom pronoun behavior for use in a specific langauge.

Deprecated
```
```

### [Structures](/documentation/Foundation/Morphology#Structures)

```swift
```swift
```swift
```swift
struct Pronoun
```
```

A custom pronoun for referring to a third person.
```
```

### [Instance Properties](/documentation/Foundation/Morphology#Instance-Properties)

```swift
```swift
```swift
```swift
var definiteness: Morphology.Definiteness?
```
```
```
```swift
```swift
```swift
var determination: Morphology.Determination?
```
```
```
```swift
```swift
```swift
var grammaticalCase: Morphology.GrammaticalCase?
```
```
```
```swift
```swift
```swift
var grammaticalPerson: Morphology.GrammaticalPerson?
```
```
```
```swift
```swift
```swift
var pronounType: Morphology.PronounType?
```
```
```
```

### [Enumerations](/documentation/Foundation/Morphology#Enumerations)

```swift
```swift
```swift
```swift
enum Definiteness
```
```
```
```swift
```swift
```swift
enum Determination
```
```
```
```swift
```swift
```swift
enum GrammaticalCase
```
```
```
```swift
```swift
```swift
enum GrammaticalPerson
```
```
```
```swift
```swift
```swift
enum PronounType
```
```
```
```

## [Relationships](/documentation/Foundation/Morphology#relationships)

### [Conforms To](/documentation/Foundation/Morphology#conforms-to)

*   [`Copyable`](/documentation/Swift/Copyable)
*   [`Decodable`](/documentation/Swift/Decodable)
*   [`Encodable`](/documentation/Swift/Encodable)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`Sendable`](/documentation/Swift/Sendable)
*   [`SendableMetatype`](/documentation/Swift/SendableMetatype)

## [See Also](/documentation/Foundation/Morphology#see-also)

### [Automatic grammar agreement](/documentation/Foundation/Morphology#Automatic-grammar-agreement)

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