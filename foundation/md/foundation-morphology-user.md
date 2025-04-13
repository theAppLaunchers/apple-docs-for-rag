

- Foundation
- Morphology
-  user 

Type Property

# user

The addressing preferences of the current user.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
static let user: Morphology
```

## Discussion

If the user hasn’t specified preferences, or chose not to share them with this app, the isUnspecified property is `true`.

This value doesn’t change throughout the lifetime of the process.

