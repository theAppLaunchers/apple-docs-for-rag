

- CloudKit
-  Enabling CloudKit in Your App 

Article

# Enabling CloudKit in Your App

Configure your app to store data in iCloud using CloudKit.

## Overview

Once you’ve determined that CloudKit is right for your app, you’re ready to set up your Xcode project to enable CloudKit development.

### Add the iCloud capability to your Xcode project

Adding the iCloud capability to your project sets up the initial project entitlements. Before you proceed, verify that your Apple Developer Program membership is active and has admin permissions.

To add the iCloud capability:

1.  In the Xcode Project navigator, select your project and your project target.

2.  Click the “Signing and Capabilities” tab and select “Automatically manage signing.”

3.  Specify your development team.

4.  Make sure that your bundle identifier is one you want to use for your app. (This identifier determines the name of the iCloud container created in a later step.)

5.  Click the + Capability button, then search for iCloud in the Add Capability editor and select that capability. An iCloud section appears on your app’s Signing and Capabilities page.

### Create your container

Next, add the CloudKit service to add the appropriate entitlements to your project and tell iCloud to create a container for your app data:

1.  Select the CloudKit checkbox. In addition to adding the CloudKit capability to your app, this selection also creates an iCloud container and adds the Push Notifications capability. The name of the container is your app’s bundle identifier prefixed with “iCloud.”

2.  Check the box next to the container name.

Multiple apps and users have access to iCloud, but each app’s data and schema, together, are typically in separate containers. Although an app can have multiple containers or share a container, each app has one default container. Once you’ve created a container, you can’t delete or rename it.

### Select or create an iCloud account for development

You need an iCloud account to save records to a container. In your app or the simulator on which you test your app during development, enter the credentials for this iCloud account. If you don’t have an iCloud account, create one for use during development. In macOS, launch System Preferences and click Sign In. Click Create Apple ID under the Apple ID text field and follow the instructions.

Note that your iCloud account is distinct from your Apple Developer account; however, you can use the same email address for both. Doing so gives you access to your iCloud account’s private user data in CloudKit Dashboard, which can be helpful for debugging.

### Enter iCloud credentials before running your app

Enter your iCloud account credentials on a simulator or app-testing device. Entering the iCloud credentials enables reading from—and writing to—users’ own private and shared databases and, potentially, writing to the container’s public database.

To enter your credentials on an iOS or iPadOS device:

1.  Launch the Settings app and click “Sign in to your iPhone/iPad.”

2.  Enter your Apple ID and password.

3.  Click Next. Wait until the system verifies your iCloud account.

4.  To enable iCloud Drive, choose iCloud and then click the iCloud Drive switch. If the switch doesn’t appear, iCloud Drive is already enabled.

Perform the same sign-in process for each iOS or iPadOS simulator you test your app on. You can access the simulators from Xcode by choosing Xcode \> Open Developer Tool \> Simulator.

To enter your credentials for macOS, go to System Preferences.

### View your container in CloudKit Console

CloudKit Console is a web-based tool that lets you manage your app’s iCloud containers. It appears within the Apple Developer web portal, and you can use it to ensure that your container exists.

1.  Using a web browser, such as Safari, navigate to the CloudKit Console webpage at https://icloud.developer.apple.com/.

2.  If you’re asked to sign in, enter your credentials and click Sign In.

3.  On the subsequent page, verify that your container appears in the container list.

For more information on CloudKit Console, see Managing iCloud Containers with CloudKit Database App.

## See Also

### Essentials

Deciding whether CloudKit is right for your app

Explore the various options you have for using iCloud to store and sync your app’s data.

