

- SwiftUI
- PencilPreferredAction
-  runSystemShortcut 

Type Property

# runSystemShortcut

An action that runs a system shortcut.

iOS 17.5+iPadOS 17.5+Mac Catalyst 17.5+macOS 14.5+

``` source
static let runSystemShortcut: PencilPreferredAction
```

## Discussion

If the user selects this as their preferred action to perform after double-tapping or squeezing their Apple Pencil, your app will never be notified when they do. Instead, you should only use this information to remind the user about their preference in your app’s UI.

