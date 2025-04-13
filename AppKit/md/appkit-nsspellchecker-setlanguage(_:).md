

- AppKit
- NSSpellChecker
-  setLanguage(\_:) 

Instance Method

# setLanguage(\_:)

Returns whether the specified language is in the Spelling pop-up list.

macOS

``` source
func setLanguage(_ language: String) -> Bool
```

## Parameters 

`language`  

The requested language.

## Return Value

true if the language is available in the pop-up list, otherwise false.

## Discussion

The code listing below shows how languages can be specified in language. If the language specified is listed in the user’s list of preferred languages, the spell checker uses that language to accomplish its task.

Listing 1. Specifying the spell checker language

```
NSSpellChecker* spell_checker = [NSSpellChecker sharedSpellChecker];

// Sets language to French. The language method returns "fr".
[spell_checker setLanguage:@"fr"];

// Sets language to the one spoken in Netherlands (English). The language method returns "en".
[spell_checker setLanguage:@"NL"];

// Sets language to British English. The language method returns "en_GB".
[spell_checker setLanguage:@"en_GB"]

 // Sets language to German. The language method returns "de".
[spell_checker setLanguage:@"German"];
```

To learn about the strings you can use to specify a language in `language`, see Language and Locale Designations in Internationalization and Localization Guide.

## See Also

### Configuring Spell Checkers Languages

var availableLanguages: [String]

Provides a list of all available languages.

var userPreferredLanguages: [String]

Provides a subset of the available languages to be used for spell checking.

var automaticallyIdentifiesLanguages: Bool

Sets whether the spell checker will automatically identify languages.

func language() -> String

Returns the current language used in spell checking.

