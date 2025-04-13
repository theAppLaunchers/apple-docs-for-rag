

- SwiftUI
-  ToolbarTitleMenu 

Structure

# ToolbarTitleMenu

The title menu of a toolbar.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
struct ToolbarTitleMenu where Content : View
```

## Overview

A title menu represents common functionality that can be done on the content represented by your app’s toolbar or navigation title. This menu may be populated from your app’s commands like saveItem or printItem.

```
ContentView()
    .toolbar {
        ToolbarTitleMenu()
    }
```

You can provide your own set of actions to override this behavior.

```
ContentView()
    .toolbar {
        ToolbarTitleMenu {
            DuplicateButton()
            PrintButton()
        }
    }
```

In iOS and iPadOS, this will construct a menu that can be presented by tapping the navigation title in the app’s navigation bar.

## Topics

### Creating a toolbar title menu

init()

Creates a toolbar title menu where actions are inferred from your apps commands.

init(content: () -> Content)

Creates a toolbar title menu.

## Relationships

### Conforms To

- CustomizableToolbarContent
- ToolbarContent

## See Also

### Setting the toolbar title menu

func toolbarTitleMenu&lt;C>(content: () -> C) -> some View

Configure the title menu of a toolbar.

