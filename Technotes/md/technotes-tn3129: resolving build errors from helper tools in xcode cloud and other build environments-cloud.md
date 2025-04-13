

- Technotes
-  TN3129: Resolving build errors from helper tools in Xcode Cloud and other build environments 

Article

# TN3129: Resolving build errors from helper tools in Xcode Cloud and other build environments

Review common causes for failing Xcode Cloud builds that originate from helper tools running in a misconfigured build environment.

## Overview

Xcode Cloud offers a continuous integration build environment that includes a macOS version and an Xcode version that you configure for each Xcode Cloud workflow. Your project or workspace may depend on helper tools beyond the tools that are included with macOS or Xcode to successfully build your app. If your app’s build requires the installation of additional helper tools into the Xcode Cloud build environment, you use a post-clone script to install the tool for every build.

You define the build environment by choosing the macOS version, the Xcode version, and helper tools that your app’s build requires. As a side effect of using helper tools, you may encounter build errors specific to these helper tools. Xcode Cloud creates a clean, temporary environment for every build, requiring you to install the helper tools during each build. As a result, installation or build errors caused by helper tools may appear more often in Xcode Cloud than locally on your Mac.

Note

To learn more about using third-party tools in Xcode Cloud, see Making dependencies available to Xcode Cloud and Writing custom build scripts.

## Review common causes for errors caused by helper tools

Apps invoking helper tools as part of the app’s build may encounter an error in a misconfigured build environment. These errors occur because of the following conditions:

- The helper tool is based on Ruby.

- The helper tool uses a native system extension to access C libraries on macOS.

- The macOS version of the build machine running the helper tool does not match the macOS SDK version provided by Xcode.

When a build meets all of these conditions, the build may fail with error messages similar to the following examples.

```
mkmf.rb can't find header files for ruby at
/System/Library/Frameworks/Ruby.framework/Versions/2.6/usr/lib/ruby/include/ruby.h
```

```
checking for ffi.h... *** extconf.rb failed ***
Could not create Makefile due to some reason, probably lack of necessary
libraries and/or headers.
```

```
/System/Library/Frameworks/Ruby.framework/Versions/2.6/usr/lib/ruby/2.6.0/mkmf.rb:467:in `try_do':
The compiler failed to generate an executable file. (RuntimeError)
You have to install development tools first.

    from /System/Library/Frameworks/Ruby.framework/Versions/2.6/usr/lib/ruby/2.6.0/mkmf.rb:1108:in `have_header'
    from extconf.rb:10:in `system_libffi_usable?'
    from extconf.rb:42:in `'
```

```
Error: Xcode alone is not sufficient on .
Install the Command Line Tools:
xcode-select --install
```

Note

If Xcode is available in the build environment, you don’t need to install the Command Line Tools package to resolve the error, because Xcode already includes the build tools provided by the Command Line Tools package.

## Review usage of the helper tool

Before attempting to resolve the error, first consider removing the helper tool from your app’s build entirely. If you build your app with Xcode Cloud, reduce the amount of additional software installed on every build to lower the build time, and receive build and test results faster.

In many cases, Xcode provides functionality that can replace the helper tool. In other cases, you can use the Swift package plugin support to add functionality in Xcode. For example, if the helper tool generates source code as part of the build, consider using or creating a Swift package plugin with this functionality instead of a separate helper tool. To use an existing package plugin, add it to your package manifest. For more information about Swift package plugins, see Meet Swift Package plugins and Create Swift Package plugins

## Adjust the Xcode Cloud build environment

If your app builds using Xcode Cloud and you are unable to remove the helper tool, try to resolve the error by modifying the Environment section of a workflow. Select the Latest Release option for both the Xcode and macOS settings. For workflows that do not release to the App Store, select Latest Beta or Release for both the Xcode and macOS settings. By selecting these options, the macOS SDK version in Xcode matches the macOS version on the build machine, which often resolves the build error. See Xcode Cloud Workflow Reference for additional information on configuring workflows.

## Manage the build environment manually

Some build environments require you to manually manage the Xcode version and macOS versions comprising the build environment to resolve the error. These environments include Macs used for development, self-managed continuous integration servers, as well as Xcode Cloud workflows that aren’t able to use the options described in Adjust the Xcode Cloud build environment. In these build environments, match the major version number of the macOS SDK in Xcode to the major version number of the macOS installation on the build machine. By matching these version numbers, the helper tool has access to the resources it needs within the macOS SDK.

For example, if you are using Xcode 13.2, which contains the macOS 12.1 SDK, the build machine must use macOS 12 so the major version numbers match (12). If you build on macOS 11, the helper tool will fail because the major SDK version (12) doesn’t match the major macOS version (11).

Note

The complete list of Xcode versions and the macOS SDK versions they contain is available on the Xcode support page.

## Revision History

- **2022-07-19** First published.

## See Also

### Latest

TN3182: Adding privacy tracking keys to your privacy manifest

Declare the tracking domains you use in your app or third-party SDK in a privacy manifest.

TN3183: Adding required reason API entries to your privacy manifest

Declare the APIs that can potentially fingerprint devices in your app or third-party SDK in a privacy manifest.

TN3184: Adding data collection details to your privacy manifest

Declare the data your app or third-party SDK collects in a privacy manifest.

TN3181: Debugging an invalid privacy manifest

Identify common configurations that cause unsuccessful privacy manifest validation with the App Store.

TN3180: Reverting to App Store Server Notifications V1

Migrate from version 2 to version 1 of App Store Server Notifications using the Modify an App endpoint.

TN3179: Understanding local network privacy

Learn how local network privacy affects your software.

TN3178: Checking for and resolving build UUID problems

Ensure that every Mach-O image has a UUID, and that every distinct Mach-O image has its own unique UUID.

TN3177: Understanding alternate audio track groups in movie files

Learn how alternate groups collect audio tracks, and how to choose which audio track to use in your app.

TN3111: iOS Wi-Fi API overview

Explore the various Wi-Fi APIs available on iOS and their expected use cases.

TN3176: Troubleshooting Apple Pay payment processing issues

Diagnose errors that occur when processing Apple Pay payments, identify common causes, and explore potential solutions.

TN3175: Diagnosing issues with displaying the Apple Pay button on your website

Diagnose common errors received while displaying the Apple Pay button on your website by identifying the underlying causes, and explore potential solutions.

TN3174: Diagnosing issues with the Apple Pay payment sheet on your website

Diagnose errors received while presenting the Apple Pay payment sheet on your website by identifying the underlying causes of common errors and explore their potential solutions.

TN3173: Troubleshooting issues with your Apple Pay merchant identifier configuration

Diagnose errors due to invalid Apple Pay merchant identifier configurations by identifying the underlying causes of common errors and explore their potential solutions.

TN3168: Making your App Clip available in the App Store

Learn how to configure your App Clip to prevent it from being unavailable in the App Store.

TN3124: Debugging coordinate space issues

Learn techniques to help debug any coordinate space issue.

