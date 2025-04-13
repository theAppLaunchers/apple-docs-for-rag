

- Swift
- Imported C and Objective-C APIs
-  Importing Objective-C into Swift 

Article

# Importing Objective-C into Swift

Access classes and other declarations from your Objective-C code in Swift.

## Overview

You can use Objective-C and Swift files together in a single project, no matter which language the project used originally. This makes creating mixed-language app and framework targets as straightforward as creating an app or framework target written in a single language.

The process for using your Objective-C declarations from your Swift code within mixed-language targets differs slightly depending on whether you’re writing an app or a framework. Both processes are described below.

### Import Code Within an App Target

To import a set of Objective-C files into Swift code within the same app target, you rely on an Objective-C bridging header file to expose those files to Swift. Xcode offers to create this header when you add a Swift file to an existing Objective-C app, or an Objective-C file to an existing Swift app.

If you accept, Xcode creates the bridging header file along with the file you were creating, and names it by using your product module name followed by `"-Bridging-Header.h"`. Alternatively, you can create a bridging header yourself by choosing File \> New \> File \> \[*operating system*\] \> Source \> Header File.

Edit the bridging header to expose your Objective-C code to your Swift code:

1.  In your Objective-C bridging header, import every Objective-C header you want to expose to Swift.

2.  In Build Settings, in Swift Compiler - General, make sure the Objective-C Bridging Header build setting has a path to the bridging header file. The path should be relative to your project, similar to the way your `Info.plist` path is specified in Build Settings. In most cases, you won’t need to modify this setting.

Any public Objective-C headers listed in the bridging header are visible to Swift. The Objective-C declarations are automatically available from any Swift file within that target, with no import statements. Use classes and other declarations from your custom Objective-C code with the same Swift syntax you use for system classes.

### Import Code Within a Framework Target

To use the Objective-C declarations in files in the same framework target as your Swift code, configure an umbrella header as follows:

1.  Under Build Settings, in Packaging, make sure the Defines Module setting for the framework target is set to Yes.

2.  In the umbrella header, import every Objective-C header you want to expose to Swift.

Swift sees every header you expose publicly in your umbrella header. The contents of the Objective-C files in that framework are automatically available from any Swift file within that framework target, with no import statements. Use classes and other declarations from your Objective-C code with the same Swift syntax you use for system classes.

## See Also

### Swift and Objective-C in the Same Project

Importing Swift into Objective-C

Access Swift types and declarations from within your Objective-C codebase.

