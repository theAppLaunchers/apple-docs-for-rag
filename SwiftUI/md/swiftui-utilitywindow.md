

- SwiftUI
-  UtilityWindow 

Structure

# UtilityWindow

A specialized window scene that provides secondary utility to the content of the main scenes of an application.

macOS 15.0+

``` source
struct UtilityWindow where Content : View
```

## Overview

Utility windows are typically used to display controls, settings, or information associated the main content of an application, sometimes referred to as tool palettes or inspector windows. Because of this role, they have specialized behavior compared to all other windows:

- They receive `FocusedValues` from the focused main scene in an application, similar to commands in the main menu, which can be used to display information on the active content as the user focuses on different scenes.

- They have a default window level of `.floating` so they remain visible when moving focus between the main scenes.

- They hide when the window is no longer active.

- They only become focused when explicitly needed, such as clicking in the titlebar or on a focusable view.

- When focused, they can be dismissed with the Escape key.

- They are not minimizable by default.

  @main struct PhotoBrowser: App { var body: some Scene { WindowGroup { PhotoGallery() }

  ```
        UtilityWindow("Photo Info", id: "photo-info") {
            PhotoInfoViewer()
        }
    }
  ```

  }

  struct PhotoInfoViewer: View { // Automatically updates to the photo selection from whichever // photo gallery window is focused. @FocusedValue(PhotoSelection.self) private var selectedPhotos

  ```
    var body: some View {
        Text("\(selectedPhotos.count) photos selected")
    }
  ```

  }

`UtilityWindow` will automatically add a menu item to show/hide itself in the “View” menu. This can be removed by applying commandsRemoved() to the utility window, and manually placing a WindowVisibilityToggle elsewhere in an app’s commands. Utility windows can also be programmatically presented with openWindow and dismissed using dismiss.

## Topics

### Initializers

init(_:id:content:)

Creates a utility window with a title and identifier.

## Relationships

### Conforms To

- Scene

## See Also

### Creating windows

struct WindowGroup

A scene that presents a group of identically structured windows.

struct Window

A scene that presents its content in a single, unique window.

protocol WindowStyle

A specification for the appearance and interaction of a window.

func windowStyle&lt;S>(S) -> some Scene

Sets the style for windows created by this scene.

