

- RealityKit
- RealityViewDefaultPlaceholder
-  keyboardShortcut(\_:) 

Instance Method

# keyboardShortcut(\_:)

Assigns a keyboard shortcut to the modified control.

RealityKitSwiftUIiOS 14.0+iPadOS 14.0+Mac CatalystmacOS 11.0+visionOS

``` source
nonisolated
func keyboardShortcut(_ shortcut: KeyboardShortcut) -> some View
```

## Discussion

Pressing the control’s shortcut while the control is anywhere in the frontmost window or scene, or anywhere in the macOS main menu, is equivalent to direct interaction with the control to perform its primary action.

The target of a keyboard shortcut is resolved in a leading-to-trailing traversal of one or more view hierarchies. On macOS, the system looks in the key window first, then the main window, and then the command groups; on other platforms, the system looks in the active scene, and then the command groups.

If multiple controls are associated with the same shortcut, the first one found is used.

