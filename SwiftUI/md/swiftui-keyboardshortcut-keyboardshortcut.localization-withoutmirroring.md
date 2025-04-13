

- SwiftUI
- KeyboardShortcut
- KeyboardShortcut.Localization
-  withoutMirroring 

Type Property

# withoutMirroring

Don’t mirror shortcuts.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+visionOS 1.0+

``` source
static let withoutMirroring: KeyboardShortcut.Localization
```

## Discussion

Use this for shortcuts that always have a specific directionality, like aligning something on the right.

Don’t use this option for navigational shortcuts like “Go Back” because navigation is flipped in right-to-left contexts.

## See Also

### Getting localization strategies

static let automatic: KeyboardShortcut.Localization

Remap shortcuts to their international counterparts, mirrored for right-to-left usage if appropriate.

static let custom: KeyboardShortcut.Localization

Don’t use automatic shortcut remapping.

