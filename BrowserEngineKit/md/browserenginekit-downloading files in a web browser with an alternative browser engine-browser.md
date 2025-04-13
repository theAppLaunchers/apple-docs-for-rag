

- BrowserEngineKit
-  Downloading files in a web browser with an alternative browser engine 

Article

# Downloading files in a web browser with an alternative browser engine

Report download progress to the system to keep your networking extension active.

## Overview

Maintaining a long-running network connection to download a large file requires your browser app’s networking extension to remain active in the background for a long period of time. Register your browser’s downloads with the system and report progress so that the system keeps your networking extension active. When the download completes, the system can optionally move the downloaded file to the person’s Downloads folder.

### Create a download progress access token

In your browser app, when someone starts a download, create a URL bookmark for the URL that represents the destination for the download, and an access token for the download progress API:

```
let destinationURL = URL(...)
let destinationData = try destinationURL.bookmarkData()
let tokenData = DownloadMonitor.createAccessToken()
```

Pass both the bookmark data and access token to your networking extension. For information about using XPC to communicate between a browser app and its extensions, see Using XPC to communicate with browser extensions.

### Register download progress with the system

In your networking extension, receive the bookmark data and resolve the download’s destination URL. Initialize a BEDownloadMonitor object with the download source URL, destination URL, access token, and a Progress object that you use to report the download’s progress to the system:

```
let destinationURL = try! URL(resolvingBookmarkData: destinationData)
let progress = Progress()
let downloadMonitor = BEDownloadMonitor(sourceURL: sourceURL, destinationURL: destinationURL, observedProgress: progress, liveActivityAccessToken: tokenData)
```

### Request that the system move the file to the person’s Downloads folder

If the system should create a placeholder file in the person’s Downloads folder that shows the state of the download, call the download monitor’s useDownloadsFolder(placeholderType:finalFileCreatedHandler:) method. Use the completion handler to receive the location to which the system moves the completed downloads, as both a URL and bookmark data:

```
downloadMonitor.useDownloadsFolder() { finalLocation in
    // Send the final location's URL and bookmark back to the browser app.
}
```

The bookmark you get in the completion handler isn’t suitable for storing to resolve later, if you need to do this then create your own bookmark with security scope. For more information, see bookmarkData(options:includingResourceValuesForKeys:relativeTo:).

### Download the file and report progress to the system

When your network extension is ready to commence the download, call beginMonitoring(). If you requested that the system use the person’s Downloads folder, this method returns the placeholder location that the system creates to host the downloaded content, as both a URL and bookmark data. Make a network connection to download the content, for example using the URL Loading System, store data in the file at the download’s destination URL, and update the `Progress` object that you passed to the `BEDownloadMonitor`:

```
var downloadCompletedWithoutError = false
let placeholderURLWithBookmark = try await downloadMonitor.beginMonitoring()

// Send the placeholder URL and bookmark back to the browser app.

// Download the file using networking APIs, and
// update progress.completedUnitCount as you write content to disk.

if (downloadCompletedWithoutError) {
    // Indicate to the system that the download is complete.
    progress.completedUnitCount = progress.totalUnitCount
} else {
    // Indicate to the system that the download is canceled.
    progress.cancel()
}
```

When you indicate that the progress is complete, if you asked the system to create a placeholder file in the person’s Downloads folder, the system calls the completion handler you passed to useDownloadsFolder(placeholderType:finalFileCreatedHandler:) to inform your browser of the downloaded file’s location in the Downloads folder. If you don’t tell the system to use the Downloads folder, beginMonitoring() returns `nil`. You still download the file to a location in your app’s container using networking APIs, but the system doesn’t show a placeholder in the Downloads folder.

## See Also

### Downloads

class BEDownloadMonitor

An object that reports the status of web downloads to the system.

