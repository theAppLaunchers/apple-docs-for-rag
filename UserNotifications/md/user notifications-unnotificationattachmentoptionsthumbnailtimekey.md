

- User Notifications
-  UNNotificationAttachmentOptionsThumbnailTimeKey 

Global Variable

# UNNotificationAttachmentOptionsThumbnailTimeKey

The frame number of an animation to use as a thumbnail image.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+macOS 10.14+visionOS 1.0+watchOS 3.0+

``` source
let UNNotificationAttachmentOptionsThumbnailTimeKey: String
```

## Discussion

For animated images, the value of this key is an NSNumber containing the frame number to use as the thumbnail. For movies, the value of this key is the time (in seconds) into the movie from which to grab the thumbnail image; you may also specify the value as a CMTime structure encoded using the CMTimeCopyAsDictionary(_:allocator:) function.

## See Also

### Creating an Attachment

convenience init(identifier: String, url: URL, options: [AnyHashable : Any]?) throws

Creates an attachment object from the specified file and options.

let UNNotificationAttachmentOptionsTypeHintKey: String

A hint about an attachment’s file type.

let UNNotificationAttachmentOptionsThumbnailHiddenKey: String

A Boolean value indicating whether the system hides the attachment’s thumbnail.

let UNNotificationAttachmentOptionsThumbnailClippingRectKey: String

The clipping rectangle for a thumbnail image.

