*   [Authentication Services](/documentation/authenticationservices)
*   Connecting to a service with passkeys

Sample Code

# Connecting to a service with passkeys

Allow users to sign in to a service without typing a password.

[Download](https://docs-assets.developer.apple.com/published/83aaf0818492/ConnectingToAServiceWithPasskeys.zip)

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+Xcode 14.0+

## [Overview](/documentation/AuthenticationServices/connecting-to-a-service-with-passkeys#Overview)

Note

This sample code project is associated with WWDC22 session [10092: Meet passkeys](https://developer.apple.com/wwdc22/10092/) and WWDC21 session [10106: Move beyond passwords](https://developer.apple.com/wwdc21/10106/).

### [Configure the sample code project](/documentation/AuthenticationServices/connecting-to-a-service-with-passkeys#Configure-the-sample-code-project)

To build and run this sample:

1.  Open the sample with Xcode 14 or later.
    
2.  Select the Shiny project.
    
3.  For the project’s target, select your team from the Team drop-down menu in the Signing & Capabilities pane to let Xcode automatically manage your provisioning profile.
    
4.  Add the Associated Domains capability using the “+ Capability” button in the same pane, and specify your domain with the `webcredentials` service.
    
5.  Ensure an `apple-app-site-association` (AASA) file is present on your domain in the `.well-known` directory, and that it contains an entry for this app’s App ID for the `webcredentials` service.
    
6.  In the `AccountManager.swift` file, replace all occurrences of `example.com` with the name of your domain.
    

## [See Also](/documentation/AuthenticationServices/connecting-to-a-service-with-passkeys#see-also)

### [Passkeys](/documentation/AuthenticationServices/connecting-to-a-service-with-passkeys#Passkeys)

[

API Reference

Public-Private Key Authentication](/documentation/authenticationservices/public-private-key-authentication)

Register and authenticate users with passkeys and security keys, without using passwords.

[

API Reference

Passkey use in web browsers](/documentation/authenticationservices/passkey-use-in-web-browsers)

Register and authenticate website users by using passkeys.

[

Performing fast account creation with passkeys](/documentation/authenticationservices/performing-fast-account-creation-with-passkeys)

Allow people to quickly create an account with passkeys and associated domains.