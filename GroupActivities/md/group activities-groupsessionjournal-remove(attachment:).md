

- Group Activities
- GroupSessionJournal
-  remove(attachment:) 

Instance Method

# remove(attachment:)

Removes the specified attachment from the journal on all sessions.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+

``` source
final func remove(attachment: GroupSessionJournal.Attachment) async throws
```

## Parameters 

`attachment`  

The attachment object associated with the item. You receive this object when you call the add(_:) or add(_:metadata:) method.

## Discussion

Call this method to remove an attachment that is no longer relevant. For example, you might remove an attachment containing a photo in response to someone deleting that photo from the activity. When you remove an attachment, the journal object updates the array of attachments and sends it to all participants. Remove any attachments from your app that aren’t still in the array.

