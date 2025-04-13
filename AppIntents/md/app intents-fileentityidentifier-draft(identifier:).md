

- App Intents
- FileEntityIdentifier
-  draft(identifier:) 

Type Method

# draft(identifier:)

Creates and returns an identifier for a draft document.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
static func draft(identifier: String) -> FileEntityIdentifier
```

## Discussion

Only use this method to initialize identifiers for documents which aren’t materialized on disk yet and don’t have a file URL.

