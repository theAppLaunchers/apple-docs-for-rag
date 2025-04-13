

- MusicKit
- MusicTokenRequestOptions
-  ignoreCache 

Type Property

# ignoreCache

An option that indicates the token provider needs to discard any cached token and generate a new token.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
static let ignoreCache: MusicTokenRequestOptions
```

## Discussion

You can add the newly generated token to an in-memory or persistent cache for faster access upon subsequent requests for this token.

