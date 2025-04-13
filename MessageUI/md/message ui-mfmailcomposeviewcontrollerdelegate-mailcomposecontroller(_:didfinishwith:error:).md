

- Message UI
- MFMailComposeViewControllerDelegate
-  mailComposeController(\_:didFinishWith:error:) 

Instance Method

# mailComposeController(\_:didFinishWith:error:)

Tells the delegate that the user wants to dismiss the mail composition view.

iOS 3.0+iPadOS 3.0+Mac Catalyst 13.1+visionOS 1.0+

``` source
optional func mailComposeController(
    _ controller: MFMailComposeViewController,
    didFinishWith result: MFMailComposeResult,
    error: (any Error)?
)
```

**Required**

## Parameters 

`controller`  

The view controller object that manages the mail composition view.

`result`  

The result of the user’s action.

`error`  

If an error occurred, this parameter contains an error object with information about the type of failure.

## Discussion

Your implementation of this method should dismiss the mail composition view. Implementation of this method is optional, but expected.

If the user has opted to send the email created by this interface, that email should be queued in the user’s Mail program by the time this method is called. If an error occurred while queueing the email message, the `error` parameter contains an error object that indicates the type of failure that occurred.

## See Also

### Responding to Email Completion

enum MFMailComposeResult

Result codes returned when the mail composition interface is dismissed.

