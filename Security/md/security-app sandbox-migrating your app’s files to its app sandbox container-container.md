

- Security
- App Sandbox
-  Migrating your app’s files to its App Sandbox container 

Article

# Migrating your app’s files to its App Sandbox container

Simplify your app’s access to documents and supporting files.

## Overview

The first time someone uses an app that uses the App Sandbox entitlement, macOS creates a container folder that the app has exclusive and unrestricted access to. The app must gain additional permissions, either by adopting extra entitlements or asking permission, to access files and folders outside this container.

If you are adopting App Sandbox in an existing app, you can configure your app to migrate existing documents, scripts, and supporting files from locations in the user’s home folder to the app’s container.

### Create a container migration manifest

The app’s container migration manifest tells macOS which files to move to the app’s container when someone launches the app for the first time with the App Sandbox entitlement.

In Xcode, create a new file of type “Property List”, name it `container-migration.plist`, and add it to your app’s target.

### Migrate existing files to the app’s container

Under the root of the `container-migration.plist` file, create a key called `Move`. Change its type to array. For each file or folder you need to move into the app’s container, add one of these two elements to the array:

- A string containing the file or folder’s original path. The operating system will copy the file (or, in the case of a folder, recursively copy it) to the same relative location in the app’s container.

- An array containing two strings: the file or folder’s original path, and the path in the container that the operating system should copy it to.

The strings you add to the can contain the following variables:

`${ApplicationSupport}`  
The folder for application support files.

`${AutosavedInformation}`  
The autosaved documents folder.

`${Caches}`  
The folder for cache files.

`${Document}` or `${Documents}`  
The Documents folder.

`${Home}`  
The home folder.

`${Library}`  
The library folder.

`${BundleId}`  
The app’s bundle identifier.

In source paths, these variables expand relative to the user’s home folder. In destination paths, they expand relative to the top level of the app’s container.

### Migrate user scripts to the standard location

If your app needs access to user scripts, add the `MigrateScriptsForApplication` key to the `container-migration.plist` file. The value for this key is a string that represents a folder name relative to the folder `Library/Scripts/Applications/` in the user’s home folder, or an array of strings representing multiple folder names. macOS moves these folders to `~/Library/Application Scripts/`.

### Create symbolic links to items outside the app’s container

If your app needs symbolic links to files or folders outside the container, add the key `Symlink` to the `container-migration.plist` file. The value for this key is an array of strings, representing paths to files or folders on the file system. The operating system creates symbolic links to those files and folders when it creates the app’s container.

Important

Without the appropriate permissions, your app can’t access files and folders outside of its container, even if there’s a symbolic link inside the container. You may need to apply a temporary entitlement to your app to gain the correct access.

### Revert the container migration for testing

To test that your app’s container migration works correctly, delete the following files and folders:

- Your app’s container, located at `~/Library/Containers/`.

- `~/Library/Application Scripts/`, if it exists.

- Any migrated scripts in `~/Library/Scripts/Applications/`.

The next time you launch your app, macOS recreates the container and migrates items again.

