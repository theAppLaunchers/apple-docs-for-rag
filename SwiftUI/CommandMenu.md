- SwiftUI
- CommandMenu

Structure

# CommandMenu

Command menus are stand-alone, top-level containers for controls that perform related, app-specific commands.

iOS 14.0+ iPadOS 14.0+ Mac Catalyst 14.0+ macOS 11.0+ visionOS 1.0+

```swift
nonisolated
struct CommandMenu<Content> where Content : View
```

## Overview

Command menus are realized as menu bar menus on macOS, inserted between the built-in View and Window menus in order of declaration. On iOS, iPadOS, and tvOS, SwiftUI creates key commands for each of a menu’s commands that has a keyboard shortcut.
```

## Topics

...

## Relationships

### Conforms To

Commands

## See Also

...