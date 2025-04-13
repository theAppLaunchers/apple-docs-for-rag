

- Bundle Resources
- Entitlements
-  com.apple.developer.mail-client 

Property List Key

# com.apple.developer.mail-client

A Boolean that indicates whether the app can act as a user’s default email client.

iOS 14.0+iPadOS 14.0+visionOS 1.0+

## Details 

Type  

boolean

## Discussion

The system launches the default mail client in iOS whenever a user opens a `mailto:` link. Since email is a critical avenue for communication, Apple requires that email apps must meet specific functional criteria aimed at ensuring private and accurate access for users.

You can use this managed entitlement to allow people to use your app as a default mail app. To request this entitlement, sign in to your developer account with the Account Holder role, go to the request access page, and fill out the form on that page.

Any app that registers as a default email client option must:

- Specify the `mailto:` scheme in its `Info.plist` file.

- Be able to send a message to any valid email recipient.

- Be able to receive a message from any email sender. Apps that provide user-controlled incoming mail screening features are permitted.

