

- SwiftUI
- Scene
-  keyboardShortcut(\_:modifiers:localization:) 

Instance Method

# keyboardShortcut(\_:modifiers:localization:)

Defines a keyboard shortcut for opening new scene windows.

macOS 13.0+

``` source
nonisolated
func keyboardShortcut(
    _ key: KeyEquivalent,
    modifiers: EventModifiers = .command,
    localization: KeyboardShortcut.Localization = .automatic
) -> some Scene
```

## Parameters 

`key`  

The key equivalent the user presses to present the scene.

`modifiers`  

The modifier keys required to perform the shortcut.

`localization`  

The localization style to apply to the shortcut.

## Return Value

A scene that can be presented with a keyboard shortcut.

## Discussion

A scene’s keyboard shortcut is bound to the command it adds for creating new windows (in the case of `WindowGroup` and `DocumentGroup`) or bringing a singleton window forward (in the case of `Window` and, on macOS, `Settings`). Pressing the keyboard shortcut is equivalent to selecting the menu command.

In cases where a command already has a keyboard shortcut, the scene’s keyboard shortcut is used instead. For example, `WindowGroup` normally creates a File \> New Window menu command whose keyboard shortcut is `⌘N`. The following code changes it to `⌥⌘N`:

```
WindowGroup {
    ContentView()
}
.keyboardShortcut("n", modifiers: [.option, .command])
```

### Localization

Provide a `localization` value to specify how this shortcut should be localized.

Given that `key` is always defined in relation to the US-English keyboard layout, it might be hard to reach on different international layouts. For example the shortcut `⌘[` works well for the US layout but is hard to reach for German users, where `[` is available by pressing `⌥5`, making users type `⌥⌘5`. The automatic keyboard shortcut remapping re-assigns the shortcut to an appropriate replacement, `⌘Ö` in this case.

Providing the option custom disables the automatic localization for this shortcut to tell the system that internationalization is taken care of in a different way.

## See Also

### Setting commands

func commands&lt;Content>(content: () -> Content) -> some Scene

Adds commands to the scene.

func commandsRemoved() -> some Scene

Removes all commands defined by the modified scene.

func commandsReplaced&lt;Content>(content: () -> Content) -> some Scene

Replaces all commands defined by the modified scene with the commands from the builder.

func keyboardShortcut(KeyboardShortcut?) -> some Scene

Defines a keyboard shortcut for opening new scene windows.

