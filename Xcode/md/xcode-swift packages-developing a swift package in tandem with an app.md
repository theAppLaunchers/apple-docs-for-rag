

- Xcode
- Swift packages
-  Developing a Swift package in tandem with an app 

Article

# Developing a Swift package in tandem with an app

Add your published Swift package as a local package to your app’s project and develop the package and the app in tandem.

## Overview

Swift packages are a convenient and lightweight solution for creating a modular app architecture and reusing code across your apps or with other developers. Over time, you may want to develop your published Swift package in tandem with your app, or create a sample app to showcase its features. To develop a Swift package in tandem with an app, you can leverage the behavior whereby a local package overrides a package dependency with the same name:

1.  Add the Swift package to your app as a package dependency instead of a local package, as described in Editing a package dependency as a local package.

2.  Develop your app and your Swift package in tandem, and push changes to their repositories.

3.  If you release a new version of your Swift package or want to stop using the local package, remove it from the project to use the package dependency again.

## See Also

### Package creation

Creating a standalone Swift package with Xcode

Bundle executable or shareable code into a standalone Swift package.

Bundling resources with a Swift package

Add resource files to your Swift package and access them in your code.

Localizing package resources

Ensure that your Swift package provides localized resources for many locales.

Distributing binary frameworks as Swift packages

Make binaries available to other developers by creating Swift packages that include one or more XCFrameworks.

Organizing your code with local packages

Simplify maintenance, promote modularity, and encourage reuse by organizing your app’s code into local Swift packages.

PackageDescription

Create reusable code, organize it in a lightweight way, and share it across your projects and with other developers.

