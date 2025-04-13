

- UIKit
- App and environment
- Responding to the launch of your app
-  Performing one-time setup for your app 

Article

# Performing one-time setup for your app

Ensure proper configuration of your app environment.

## Overview

When the user launches your app for the first time, you might want to prepare your app environment by performing some one-time tasks. For example, you might want to:

- Download required data from your server.

- Copy document templates or modifiable data files from your app bundle to a writable directory.

- Configure default preferences for the user.

- Set up user accounts or gather other required data.

Perform any one-time tasks in your app delegate’s application(_:willFinishLaunchingWithOptions:) or application(_:didFinishLaunchingWithOptions:) method. Never block the app’s main thread for tasks that don’t require user input. Instead, start tasks asynchronously using a dispatch queue, and let them run in the background while your app finishes launching. For tasks that require user input, make all changes to your user interface in the application(_:didFinishLaunchingWithOptions:) method.

### Install files in the proper locations

Your app has its own container directory for storing files, and you should always place app-specific files in the `~/Library` subdirectory. Specifically, store your files in the following `~/Library` subdirectories:

- `~/Library/Application Support/` — Store app-specific files that you want backed up with the user’s other content. (You can create custom subdirectories here as needed.) Use this directory for data files, configuration files, document templates, and so on.

- `~/Library/Caches/` — Store temporary data files that can be easily regenerated or downloaded.

To obtain a URL for one of the directories in your app’s container, use the urls(for:in:) method of FileManager.

```
let appSupportURL = FileManager.default.urls(for: 
      .applicationSupportDirectory, in: .userDomainMask)

let cachesURL = FileManager.default.urls(for: 
      .cachesDirectory, in: .userDomainMask)
```

Place any temporary files in your app’s `tmp/` directory. Temporary files might include compressed files that you intend to delete once their contents have been extracted and installed elsewhere. Retrieve the URL for your app’s temporary directory using the temporaryDirectory method of FileManager.

## See Also

### Launch time

About the app launch sequence

Learn the order in which the system executes your code at app launch time.

Preserving your app’s UI across launches

Return your app to its previous state after the system terminates it.

