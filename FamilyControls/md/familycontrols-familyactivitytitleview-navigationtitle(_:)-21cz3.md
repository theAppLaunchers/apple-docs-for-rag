

- FamilyControls
- FamilyActivityTitleView
-  navigationTitle(\_:) 

Instance Method

# navigationTitle(\_:)

Configures the view’s title for purposes of navigation, using a string.

FamilyControlsSwiftUIiOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 14.0+watchOS 7.0+

``` source
nonisolated
func navigationTitle(_ title: S) -> some View where S : StringProtocol
```

## Parameters 

`title`  

The string to display.

## Discussion

A view’s navigation title is used to visually display the current navigation state of an interface. On iOS and watchOS, when a view is navigated to inside of a navigation view, that view’s title is displayed in the navigation bar. On iPadOS, the primary destination’s navigation title is reflected as the window’s title in the App Switcher. Similarly on macOS, the primary destination’s title is used as the window title in the titlebar, Windows menu and Mission Control.

Refer to the doc:Configure-Your-Apps-Navigation-Titles article for more information on navigation title modifiers.

