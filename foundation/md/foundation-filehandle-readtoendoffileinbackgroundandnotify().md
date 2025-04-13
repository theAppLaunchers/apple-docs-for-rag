

- Foundation
- FileHandle
-  readToEndOfFileInBackgroundAndNotify() 

Instance Method

# readToEndOfFileInBackgroundAndNotify()

Reads to the end of file from the file or communications channel in the background and posts a notification when finished.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func readToEndOfFileInBackgroundAndNotify()
```

## Discussion

This method performs an asynchronous `readToEndOfFile` operation on a file or communications channel and posts an NSFileHandleReadToEndOfFileCompletion. You must call this method from a thread that has an active run loop.

The notification includes a `userInfo` dictionary that contains the data read; access this object using the `NSFileHandleNotificationDataItem` key.

Any object interested in receiving this data asynchronously must add itself as an observer of NSFileHandleReadToEndOfFileCompletion. In communication via stream-type sockets, the receiver is often the object returned in the `userInfo` dictionary of NSFileHandleConnectionAccepted.

## See Also

### Related Documentation

func enqueue(Notification, postingStyle: NotificationQueue.PostingStyle, coalesceMask: NotificationQueue.NotificationCoalescing, forModes: [RunLoop.Mode]?)

Adds a notification to the notification queue with a specified posting style, criteria for coalescing, and run loop mode.

### Reading Asynchronously with Notifications

func acceptConnectionInBackgroundAndNotify()

Accepts a socket connection (for stream-type sockets only) in the background and creates a file handle for the “near” (client) end of the communications channel.

func acceptConnectionInBackgroundAndNotify(forModes: [RunLoop.Mode]?)

Accepts a socket connection (for stream-type sockets only) in the background and creates a file handle for the “near” (client) end of the communications channel.

func readInBackgroundAndNotify()

Reads from the file or communications channel in the background and posts a notification when finished.

func readInBackgroundAndNotify(forModes: [RunLoop.Mode]?)

Reads from the file or communications channel in the background and posts a notification when finished.

func readToEndOfFileInBackgroundAndNotify(forModes: [RunLoop.Mode]?)

Reads to the end of file from the file or communications channel in the background and posts a notification when finished.

func waitForDataInBackgroundAndNotify()

Asynchronously checks to see if data is available.

func waitForDataInBackgroundAndNotify(forModes: [RunLoop.Mode]?)

Asynchronously checks to see if data is available.

