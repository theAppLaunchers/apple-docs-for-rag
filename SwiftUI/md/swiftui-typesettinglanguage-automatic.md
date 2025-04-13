

- SwiftUI
- TypesettingLanguage
-  automatic 

Type Property

# automatic

Automatic language behavior.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

``` source
static let automatic: TypesettingLanguage
```

## Discussion

When determining the language to use for typesetting the current UI language and preferred languages will be considered. For example, if the current UI locale is for English and Thai is included in the preferred languages then line heights will be taller to accommodate the taller glyphs used by Thai.

## See Also

### Getting language behavior

static func explicit(Locale.Language) -> TypesettingLanguage

Use explicit language.

