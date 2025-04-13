

- Message UI
- MFMessageComposeViewController
-  isSupportedAttachmentUTI(\_:) 

Type Method

# isSupportedAttachmentUTI(\_:)

Indicates whether or not the message can accept a file, with the specified UTI, as an attachment.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+visionOS 1.0+

``` source
@MainActor
class func isSupportedAttachmentUTI(_ uti: String) -> Bool
```

## Parameters 

`uti`  

The UTI (Uniform Type Identifier) in question. See Uniform Type Identifiers Reference

## Return Value

true if a file with the specified UTI can be attached to the message, or false otherwise.

## See Also

### Determining if message composition is available

class func canSendText() -> Bool

Returns a Boolean value that indicates whether the current device is capable of sending text messages.

class func canSendAttachments() -> Bool

Indicates whether or not messages can include attachments.

class func canSendSubject() -> Bool

Indicates whether or not messages can include subject lines, according to the user’s configuration in Settings.

