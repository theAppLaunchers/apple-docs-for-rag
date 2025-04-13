

- AppKit
- NSResponder
-  presentError(\_:modalFor:delegate:didPresent:contextInfo:) 

Instance Method

# presentError(\_:modalFor:delegate:didPresent:contextInfo:)

Presents an error alert to the user as a document-modal sheet attached to document window.

macOS

``` source
@MainActor
func presentError(
    _ error: any Error,
    modalFor window: NSWindow,
    delegate: Any?,
    didPresent didPresentSelector: Selector?,
    contextInfo: UnsafeMutableRawPointer?
)
```

## Parameters 

`error`  

The object encapsulating information about the error.

`window`  

The window object identifying the window owning the document-modal sheet.

`delegate`  

The modal delegate for the sheet.

`didPresentSelector`  

A selector identifying the message to be sent to the modal delegate. The `didPresentSelector` selector must have the signature:

```
- (void)didPresentErrorWithRecovery:(BOOL)didRecover
   contextInfo:(void *)contextInfo
```

`contextInfo`  

Supplemental data to be passed to the modal delegate; can be `NULL`.

## Discussion

The information displayed in the alert is extracted from the NSError object `error`; it may include a description, recovery suggestion, failure reason, and button titles (all localized). Once the user dismisses the alert and any recovery attempter associated with the error object has had a chance to recover from it, the receiver sends a message identified by `didPresentSelector` to the modal delegate `delegate`. (A recovery attempter is an object that conforms to the NSErrorRecoveryAttempting informal protocol.)

The modal delegate implements the method identified by `didPresentSelector` to perform any post-error processing if recovery failed or was not attempted (that is, `didRecover` is false). Any supplemental data is passed to the modal delegate via `contextInfo`.

The default implementation of this method sends willPresentError(_:) to `self`. By doing this, `NSResponder` gives subclasses an opportunity to customize error presentation. It then forwards the message, passing any customized error to the next responder or, if there is no next responder, it passes the error object to `NSApp`, which displays a document-modal error alert. When the user dismisses the alert, any recovery attempter associated with the error object is given a chance to recover from the error. See the class description for the precise route up the responder chain (plus document and controller objects) this message might travel.

It is not recommended that you attempt to override this method. If you wish to customize the error presentation, override willPresentError(_:) instead.

## See Also

### Presenting and Customizing Error Information

func presentError(any Error) -> Bool

Presents an error alert to the user as an application-modal dialog.

func willPresentError(any Error) -> any Error

Returns a custom version of the supplied error object that’s more suitable for presentation in alert sheets and dialogs.

