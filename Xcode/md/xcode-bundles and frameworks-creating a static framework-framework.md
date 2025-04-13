

- Xcode
- Bundles and frameworks
-  Creating a static framework 

Article

# Creating a static framework

Configure your project to build a new static framework.

## Overview

In Xcode 15 or later, you can use a static framework to bundle resources with a static library. A static framework is a framework bundle whose main binary is a static archive. When a client links and embeds the framework, Xcode 15 or later omits the main binary from the embedded framework bundle because it’s already statically linked into the client. To create a static framework in Xcode, create a new framework target, configure the new target as a static framework target, and add all your source files and resources to the new framework target. Build, analyze, and test your static framework for each platform that it supports.

To distribute your static framework, configure its target for distribution in Xcode, then create an archive of your framework for each platform that it supports. Package all variants of your framework into an XCFramework bundle that you can sign. For more information about configuring and archiving your static framework for distribution, and creating an XCFramework bundle, see Creating a multiplatform binary framework bundle. Xcode verifies if your static framework’s code signature is tampered or becomes invalid. For more information about verifying XCFrameworks, see Verifying the origin of your XCFrameworks.

### Add a new framework target to your project

You can add the new framework target to an existing Xcode project. Create a framework that supports either a single platform or multiple platforms.

To add a new framework target:

1.  Choose File \> New \> Target.

2.  In the sheet that appears, choose the platform you wish to support. To create a framework that supports a single platform, choose that platform in the sheet. To create a framework that supports multiple platforms, choose Multiplatform in the sheet.

3.  Scroll down to the Framework & Library section.

4.  Select the Framework template.

5.  Click Next.

6.  Specify the name of your framework and configure the language and other options.

7.  Click Finish.

When you create a new framework target from a template, Xcode adds a target that builds a dynamic framework automatically. It also adds an umbrella header to the target. The header’s name is generated from your framework name, followed by a dot and the letter *h*. For example, if you name your framework SampleFramework, Xcode automatically adds a header file with the name `SampleFramework.h` to the target.

### Convert the new framework target from dynamic to static

After adding the new framework target to your Xcode project, set its Mach-O Type build setting to Static Library to convert it from dynamic to static. For more information about the Mach-O Type build setting, see the Build settings reference.

To edit the Mach-O Type build setting:

1.  In the project editor, select your new framework target, then click Build Settings.

2.  Enter “Mach-O Type” in the search field to locate the Mach-O Type build setting.

3.  Choose Static Library from the setting value list.

### Add source files to your framework target

After you have a static framework target, add new or existing source files, such as Swift files, to the target. After adding them, check that these files appear in the Compile Sources build phase of the static framework target. For more information on adding new or existing files to a target, see Managing files and folders in your Xcode project.

### Add resources to your framework target

You can add resources such as asset catalogs, storyboards, image files, and a privacy manifest to a static framework. The resource files appear in the Copy Bundle Resources build phase of the static framework target. The following image shows the Copy Bundle Resources build phase of a static framework that includes a privacy manifest file:

To add a privacy manifest to your static framework in Xcode, see Privacy manifest files.

### Add public and private headers to your framework target

If your static framework target contains public or private headers that you want to make available to external clients, add a Headers build phase to your target, then drag these files into Headers. For more information about adding public and private headers to a target, see Customizing the build phases of a target.

Additionally, add your public headers to your framework umbrella header.

### Build, analyze, and test your framework

Build, analyze, and test your static framework for each platform that it supports. The example below shows the bundle structure of `SampleFramework` after building it for iOS:

- Image
- Bundle structure

```
```

To test your static framework, create a release build of your framework, then embed it in an app that utilizes it. For more information about creating a release build of your static framework, see Testing a release build. Build and run the test app.

### Embed your framework in an app

To embed your static framework in an app:

1.  In the project editor, select the app target, then click General.

2.  Expand the Frameworks, Libraries, and Embedded Content section.

3.  Click the Add button (+), select Add Other, then choose Add Files to locate your static framework.

4.  Click Open.

5.  Choose the Embed & Sign option from the Embed value list for the static framework.

## See Also

### Frameworks

Creating a multiplatform binary framework bundle

Combine variants of a binary framework or library into an XCFramework bundle that supports multiple platforms.

Identifying and addressing framework module issues

Detect and fix common problems found in framework modules with the module verifier.

