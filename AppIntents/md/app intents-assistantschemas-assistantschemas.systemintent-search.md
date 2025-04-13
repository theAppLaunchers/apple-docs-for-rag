

- App Intents
- AssistantSchemas
- AssistantSchemas.SystemIntent
-  search 

Instance Property

# search

The app intent conforms to the schema for search functionality.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
var search: some AssistantSchemas.Intent { get }
```

## Mentioned in 

Making in-app search actions available to Siri and Apple Intelligence

## Overview

To integrate your app’s functionality with Siri and Apple Intelligence, you use Swift macros that generate additional properties and add protocol conformance for your app intent implementation.

For more information about the `.system` app intent domain, see Making in-app search actions available to Siri and Apple Intelligence. For general information about app intent domains, see Integrating actions with Siri and Apple Intelligence.

The following example shows an app intent that conforms to the `.system.search` schema:

```
@AssistantIntent(schema: .system.search)
struct SystemSearchIntent: ShowInAppSearchResultsIntent {
    static let searchScopes: [StringSearchScope] = [.general]

    @Parameter
    var criteria: StringSearchCriteria

    func perform() async throws -> some IntentResult {
        .result()
    }
}
```

