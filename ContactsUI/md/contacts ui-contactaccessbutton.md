

- Contacts UI
-  ContactAccessButton 

Structure

# ContactAccessButton

A SwiftUI button that you use to add to the set of contacts someone shares with your app.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+

``` source
@MainActor @preconcurrency
struct ContactAccessButton
```

## Overview

When someone’s using your app, they can choose to give the app full access to their contacts or to a subset of contacts. They choose this subset of contacts the first time your app requests access with requestAccess(for:completionHandler:), and can update them in the Settings app. You use this button to prompt them to authorize additional contacts for your app to use while operating under limited-access authorization.

Use this button in addition to a search UI in your app, such as a text field. Initialize the button with a query string from your search UI, along with email addresses and phone numbers to ignore. If a single contact matches, the button shows that contact’s name and image, and tapping the button grants your app access to that contact. If multiple contacts match, tapping the button navigates to another view where the person can choose which contacts to allow. The button updates its display as the query string changes; using a query string bound to a SwiftUI TextField allows the button to update its display of matches in real time as the person types.

Note

This button is only useful when your app has limited or no access to contacts. To see what level of access your app has to a person’s contacts, call authorizationStatus(for:). If the returned value is CNAuthorizationStatus.limited, the button updates itself to show partial or single matches based on the query string. If the authorization status is CNAuthorizationStatus.denied, the button shows a prompt to allow access to contacts. If the authorization status is CNAuthorizationStatus.authorized, the button doesn’t appear at all.

To show a picker of all contacts and allow someone to add them to your app, without presenting your own search UI, use contactAccessPicker(isPresented:completionHandler:).

## Topics

### Creating a contact access button

init(queryString: String, ignoredEmails: Set&lt;String>?, ignoredPhoneNumbers: Set&lt;String>?, approvalCallback: (([String]) -> ())?)

Creates a contact access button to quickly add contacts under limited-access authorization.

### Setting the button caption

enum Caption

A list of access options to display in the contact access button when matching a contact’s name.

### Accessing button style

struct Style

A type that customizes the style of a contact access button.

## Relationships

### Conforms To

- Sendable
- View

