

- Security
-  Password AutoFill 

# Password AutoFill

Streamline your app’s login and onboarding procedures.

## Overview

Password AutoFill simplifies login and account creation tasks for iOS apps and webpages. With just a few taps, your users can create and save new passwords or log in to an existing account. Users don’t even need to know their password; the system handles everything. This convenience increases the likelihood that users will complete your app’s onboarding process and start using your app more quickly. Additionally, by encouraging users to select unique, strong passwords, you increase the security of your app.

By default, Password AutoFill saves the user’s login credentials on their current iOS device. iOS can sync these credentials securely across the user’s devices using iCloud Keychain. Password AutoFill recommends credentials only for your app’s associated domain, and the user must authenticate using Face ID or Touch ID before accessing these credentials. For more information on privacy and security, see Approach to Privacy and iOS Security Guide.

Password AutoFill also provides credentials from third-party password managers that implement a credential provider extension. For more information on the credential provider extension, see the Authentication Services framework.

### Enable Password AutoFill

Password AutoFill uses heuristics to determine when the user logs in or creates new passwords, and automatically provides the password QuickType bar. These heuristics give users some Password AutoFill support in most apps, even if those apps haven’t been updated to support AutoFill. However, to provide the best user experience and ensure your app fully supports Password AutoFill, perform the following steps:

1.  Set up your app’s associated domains. To learn how to set up your app’s associated domains, see Supporting associated domains.

2.  Set the correct AutoFill type on relevant text fields. For an iOS app, see Enabling Password AutoFill on a text input view. For a web app, see Enabling Password AutoFill on an HTML input element.

### Support third-party web services

Password AutoFill streamlines logging into web services at your domain; however, if you need to log into a third-party service, use ASWebAuthenticationSession instead, which supports Password AutoFill when your user hasn’t already logged in.

### Integrate a password management app with Password AutoFill

If you’re developing a password management app, create AutoFill Credential Provider Extensions to surface credentials from your app in Password AutoFill and pull your app’s password data into the Password AutoFill workflow. When your app integrates with Password AutoFill, users don’t have to copy and paste credentials. Instead, they can use password data stored in your app easily because the data will be offered to the user to fill in compatible user name and password fields. To integrate a password app with Password AutoFill, use in the Authentication Services framework.

## Topics

### Essentials

About the Password AutoFill workflow

Learn how Password AutoFill interacts with both iOS and web apps.

Supporting associated domains

Connect your app and a website to provide both a native app and a browser experience.

object applinks

The root object for a universal links service definition.

### Text input views

Enabling Password AutoFill on a text input view

Make sure a text input view displays the correct AutoFill suggestions.

@MainActor optional var textContentType: UITextContentType! { get set }

The semantic meaning for a text input area.

static let username: UITextContentType

A property that defines the content in a text input area as an account or login name.

static let password: UITextContentType

A property that defines the content in a text input area as a password.

static let newPassword: UITextContentType

A property that defines the content in a text input area as a new password.

static let oneTimeCode: UITextContentType

A property that defines the content in a text input area as a one-time code.

### Text input elements

Enabling Password AutoFill on an HTML input element

Make sure a web view or webpage provides the correct AutoFill suggestions.

### Password rules

Customizing Password AutoFill rules

Modify the strong password rules for your app by adding your own restrictions.

@NSCopying @MainActor optional var passwordRules: UITextInputPasswordRules? { get set }

@MainActor class UITextInputPasswordRules

A class that represents password rules for a text input field.

