

- Message UI
- MFMessageComposeViewController
-  canSendAttachments() 

Type Method

# canSendAttachments()

Indicates whether or not messages can include attachments.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+visionOS 1.0+

``` source
@MainActor
class func canSendAttachments() -> Bool
```

## Return Value

true if the device can send attachments in MMS or iMessage messages, or false otherwise.

## See Also

### Determining if message composition is available

class func canSendText() -> Bool

Returns a Boolean value that indicates whether the current device is capable of sending text messages.

class func canSendSubject() -> Bool

Indicates whether or not messages can include subject lines, according to the user’s configuration in Settings.

class func isSupportedAttachmentUTI(String) -> Bool

Indicates whether or not the message can accept a file, with the specified UTI, as an attachment.

