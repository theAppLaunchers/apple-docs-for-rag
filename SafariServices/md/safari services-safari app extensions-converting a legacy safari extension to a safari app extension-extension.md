

- Safari Services
- Safari app extensions
-  Converting a legacy Safari extension to a Safari app extension 

Article

# Converting a legacy Safari extension to a Safari app extension

Convert a legacy Safari extension to a Safari app extension, automatically with keys or manually.

## Overview

When you distribute your Safari app extension, you may want it to completely replace your previously provided legacy Safari extensions. Two options are available:

- Configure your Safari app extension to provide a clean upgrade path that automatically removes the previous legacy Safari extension when installing the Safari app extension.

- Manually convert your legacy Safari extension to a Safari app extension.

### Convert legacy Safari extensions automatically

Add the `SFSafariExtensionBundleIdentifiersToUninstall` key to the `NSExtension` element inside your app extension’s `Info.plis`t file. It specifies any legacy Safari extensions that you want to remove when your Safari app extension loads. The value for this key is an array of strings, each of which is the bundle identifier of a legacy Safari extension that you want to remove.

Note

The legacy Safari extension you’re replacing must have been created by the same developer account that you use to create the Safari app extension.

When your app installs, the Safari app extension installs with it, and the system removes the legacy Safari extensions you include in the `Info.plist` file from Safari. If any of the legacy Safari extensions are enabled when the upgrade occurs, the Safari app extension is also enabled.

### Convert legacy Safari extensions manually

If you already have a legacy Safari extension and you want to convert it to a Safari app extension, you need to modify parts of it and completely rewrite others. The lists below describe these changes:

Modifications are required in these areas:

- **Context menu item validation.** Specify these items statically. In a Safari app extension, there’s no validation of contextual menu items before the menu appears.

- **Number of toolbar items.** You can have only one toolbar item. In a Safari app extension, the system statically determines the image to display in the toolbar at build time.

- **Extension bars.** Remove any extension bars from your legacy Safari extension. A Safari app extension can’t create extension bars.

Rewrites are required in these areas:

- **Using an** `Info.plist` **file.** Create an Xcode project for your Safari app extension. For data that you previously entered in the Safari Extension Builder interface, enter it instead in the app extension’s `Info.plist` file. For more information, see Safari app extension information property list keys.

- **Working in the native app extension.** A Safari app extension doesn’t have a global HTML page. Instead, pass messages from your injected code into the app extension.

- **Sending messages.** In legacy Safari extensions, you used a `safari.application.activeBrowserWindow.activeTab.page` object to send messages. In a Safari app extension, if you specify user data when sending a message, the data must be a dictionary object. For more information about the message-handling process in the native app extension, see Passing messages between Safari app extensions and injected scripts.

- **Creating popovers.** Use AppKit views and view controllers to create popovers in native code.

## See Also

### Essentials

Building a Safari app extension

Add, build, and enable a Safari app extension.

Troubleshooting your Safari app extension

Debug your Safari app extension with these techniques.

