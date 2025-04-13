

- SwiftUI
- MaterialActiveAppearance
-  automatic 

Type Property

# automatic

Materials will automatically appear active or inactive based on context and platform convention.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
static let automatic: MaterialActiveAppearance
```

## Discussion

Examples of automatic behavior on macOS:

- Materials used as a `window` container background will appear inactive when the containing window is inactive.

- `Material.bar` materials will appear inactive when the containing window is inactive.

- All other materials will appear as active.

Materials always appear as active on all other platforms.

