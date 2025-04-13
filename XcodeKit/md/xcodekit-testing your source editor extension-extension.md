

- XcodeKit
-  Testing Your Source Editor Extension 

Article

# Testing Your Source Editor Extension

Launch a special instance of Xcode to test your source editor extension.

## Overview

Source editor extensions run in a separate instance of Xcode to help prevent mistakes in your in-progress extension from interfering with your development environment.

### Test the Source Editor Extension

Test a source editor extension you’re developing by running your project when your extension’s scheme is selected. A dialog appears, asking you to choose an app to run.

Choose Xcode, and your source editor extension is initialized inside the second instance of Xcode. You can tell the two instances of Xcode apart based on the background color of the app icons. The instance of Xcode that’s running your source editor extension has a black background rather than the lighter blue background of the first instance.

To test commands defined by your extension, open a source file in the test instance of Xcode. All of the commands defined by your extension appear in the Editor menu, nested under your extension’s name. Selecting a command causes the perform(with:completionHandler:) method defined in your extension to be called with a command invocation that specifies a command identifier corresponding to that command.

While you test your source editor extension, the original instance of Xcode continues running. Use it to debug or to view console output from the extension you’re testing.

## See Also

### Related Documentation

class XCSourceEditorCommandInvocation

An object that identifies the command issued to your extension and provides the contents of the active source editor.

### Essentials

Creating a Source Editor Extension

Add and configure a source editor extension in your Xcode project.

protocol XCSourceEditorExtension

The protocol you implement to create Xcode source editor extensions.

