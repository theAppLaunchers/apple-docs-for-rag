

- SwiftUI
- View
-  typesettingLanguage(\_:isEnabled:) 

Instance Method

# typesettingLanguage(\_:isEnabled:)

Specifies the language for typesetting.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

``` source
nonisolated
func typesettingLanguage(
    _ language: Locale.Language,
    isEnabled: Bool = true
) -> some View
```

Show all declarations

## Parameters 

`language`  

The explicit language to use for typesetting.

`isEnabled`  

A Boolean value that indicates whether text language is added

## Return Value

A view with the typesetting language set to the value you supply.

## Discussion

In some cases `Text` may contain text of a particular language which doesn’t match the device UI language. In that case it’s useful to specify a language so line height, line breaking and spacing will respect the script used for that language. For example:

```
Text(verbatim: "แอปเปิล")
    .typesettingLanguage(.init(languageCode: .thai))
```

Note: this language does not affect text localization.

## See Also

### Localizing text

Preparing views for localization

Specify hints and add strings to localize your SwiftUI views.

struct LocalizedStringKey

The key used to look up an entry in a strings file or strings dictionary file.

var locale: Locale

The current locale that views should use.

struct TypesettingLanguage

Defines how typesetting language is determined for text.

