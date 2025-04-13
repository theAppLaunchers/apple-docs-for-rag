

- MailKit
- MEComposeSessionHandler
-  annotateAddressesForSession(\_:completion:) 

Instance Method

# annotateAddressesForSession(\_:completion:)

Indicates whether recipients in the compose window are valid or not.

macOS 12.0+

``` source
@MainActor
optional func annotateAddressesForSession(
    _ session: MEComposeSession,
    completion completionHandler: @escaping ([MEEmailAddress : MEAddressAnnotation]) -> Void
)
```

``` source
@MainActor
optional func annotateAddressesForSession(_ session: MEComposeSession) async -> [MEEmailAddress : MEAddressAnnotation]
```

## Parameters 

`session`  

The session that represents the properties of the message in the compose window.

`completionHandler`  

A block you call with a dictionary that contains annotation objects for recipient email addresses.

## Discussion

Important

You can call this method from synchronous code using a completion handler, as shown on this page, or you can call it as an asynchronous method that has the following declaration:

```
optional func annotateAddressesForSession(_ session: MEComposeSession) async -> [MEEmailAddress : MEAddressAnnotation]
```

For information about concurrency and asynchronous code in Swift, see Calling Objective-C APIs Asynchronously.

As the user enters recipients for a mail message, MailKit invokes this method to allow your extension to provide feedback about the validity of recipient email addresses. The status you provide indicates one of the following:

- The address is valid and correct.

- The address is invalid or may result in failure to deliver, such as the address of an employee who is no longer at your company.

- The address may not be valid and needs attention, such as an address outside of your company’s domain.

Mail displays the status in the address field using a status icon and color. In addition to the validity, you provide a localized string with additional information that Mail displays to the user.

To provide status, iterate through the addresses available in the mailMessage property of the `session` parameter. For addresses that are meaningful to your extension, determine the current status and add a MEAddressAnnotation to the dictionary you pass to the completion block.

Important

If an address isn’t meaningful to your extension and you can’t provide accurate status, ignore the address. Don’t indicate an address is valid unless you can confirm its validity.

The following code shows how to mark recipients with email addresses using `@example.com` as invalid.

```
func annotateAddressesForSession(_ session: MEComposeSession) async -> [String : MEAddressAnnotation] {
    var annotations: [String: MEAddressAnnotation] = [:]

    // Iterate through all the recipient email addresses.
    for address in session.mailMessage.allRecipientAddresses {
        // Check if it has an @example.com domain.
        if address.hasSuffix("@example.com") {
            // Create an annotation with detail about why the address is invalid.
            let message = "example.com is not a valid domain"
            let annotation = MEAddressAnnotation.error(withLocalizedDescription: message)

            // Add the annotation to the dictionary.
            annotations[address] = annotation
        }
    }

    return annotations
}
```

## See Also

### Annotating Email Address Tokens

class MEAddressAnnotation

An object that indicates the validity of an email address.

