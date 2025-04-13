

- XcodeKit
-  Creating a Source Editor Extension 

Article

# Creating a Source Editor Extension

Add and configure a source editor extension in your Xcode project.

## Overview

You build extensions to the source editor in Xcode using XcodeKit. Source editor extensions can read and modify the contents of a source file, as well as read and modify the current text selection within the editor.

### Create a New macOS Project in Xcode

To create a source editor extension, begin by creating a new macOS project in Xcode. Add a new Xcode Source Editor Extension target to your project, as shown in the figure below, and activate its associated scheme when prompted. The project now contains an additional source folder with files from the template for source editor extensions.

Because your extension runs in Xcode, you must enable development signing for each target in your project. For more information about code signing for projects during development, see App Distribution Quick Start.

The template in your new extension creates the `SourceEditorCommand` class. This class makes your code conform to the XCSourceEditorCommand protocol, so Xcode can associate a command with your code. The perform(with:completionHandler:) method is the entry point for handling commands defined in your extension. This method is called each time a user selects one of your extension’s commands from the Editor menu.

### Add Customizable Behavior

Add customizable behavior to your source editor extension by filling in the body of the perform(with:completionHandler:) method. The following example shows a command that reverses the order of the lines in a source editor:

```
```

The extension template is configured by default to define just one command. To change its name or to add more commands, edit your extension target’s `Info.plist` file.

For information on adding and configuring additional commands, see XCSourceEditorCommandDefinitionKey.

## See Also

### Essentials

Testing Your Source Editor Extension

Launch a special instance of Xcode to test your source editor extension.

protocol XCSourceEditorExtension

The protocol you implement to create Xcode source editor extensions.

