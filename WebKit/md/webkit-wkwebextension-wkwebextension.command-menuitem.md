

- WebKit
- WKWebExtension
- WKWebExtension.Command
-  menuItem 

Instance Property

# menuItem

A menu item representation of the web extension command for use in menus.

iOS 18.4+iPadOS 18.4+Mac Catalyst 18.4+macOS 15.4+visionOS 2.4+

**iOS, iPadOS, Mac Catalyst, visionOS**

``` source
@NSCopying @MainActor
var menuItem: UIMenuElement { get }
```

**macOS**

``` source
@NSCopying @MainActor
var menuItem: NSMenuItem { get }
```

## Discussion

Provides a representation of the web extension command as a menu item to display in the app.

Selecting the menu item will perform the command, offering a convenient and visual way for users to execute this web extension command.

