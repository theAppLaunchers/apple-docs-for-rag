

- FinanceKitUI
- TransactionPicker
-  handlesExternalEvents(preferring:allowing:) 

Instance Method

# handlesExternalEvents(preferring:allowing:)

Specifies the external events that the view’s scene handles if the scene is already open.

FinanceKitUISwiftUIiOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+

``` source
nonisolated
func handlesExternalEvents(
    preferring: Set,
    allowing: Set
) -> some View
```

## Parameters 

`preferring`  

A set of strings that SwiftUI compares against the incoming user activity or URL to see if the view’s scene prefers to handle the external event.

`allowing`  

A set of strings that SwiftUI compares against the incoming user activity or URL to see if the view’s scene can handle the exernal event.

## Return Value

A view whose enclosing scene — if already open — handles incoming external events.

## Discussion

Apply this modifier to a view to indicate whether an open scene that contains the view handles specified user activities or URLs that your app receives. Specify two sets of string identifiers to distinguish between the kinds of events that the scene *prefers* to handle and those that it *can* handle. You can dynamically update the identifiers in each set to reflect changing app state.

When your app receives an event on a platform that supports multiple simultaneous scenes, SwiftUI sends the event to the first open scene it finds that prefers to handle the event. Otherwise, it sends the event to the first open scene it finds that can handle the event. If it finds neither — including when you don’t add this view modifier — SwiftUI creates a new scene for the event.

Important

Don’t confuse this view modifier with the `Scene/handlesExternalEvents(matching:)` *scene* modifier. You use the view modifier to indicate that an open scene handles certain events, whereas you use the scene modifier to help SwiftUI choose a new scene to open when no open scene handles the event.

On platforms that support only a single scene, SwiftUI ignores this modifier and sends all external events to the one open scene.

### Matching an event

To find an open scene that handles a particular external event, SwiftUI compares a property of the event against the strings that you specify in the `preferring` and `allowing` sets. SwiftUI examines the following event properties to perform the comparison:

- For an NSUserActivity, like when your app handles Handoff, SwiftUI uses the activity’s targetContentIdentifier property, or if that’s `nil`, its webpageURL property rendered as an absoluteString.

- For a URL, like when another process opens a URL that your app handles, SwiftUI uses the URL’s absoluteString.

For both parameter sets, an empty set of strings never matches. Similarly, empty strings never match. Conversely, as a special case, the string that contains only an asterisk (`*`) matches anything. The modifier performs string comparisons that are case and diacritic insensitive.

If you specify multiple instances of this view modifier inside a single scene, the scene uses the union of the respective `preferring` and `allowing` sets from all the modifiers.

### Handling a user activity in an open scene

As an example, the following view — which participates in Handoff through the `View/userActivity(_:isActive:_:)` and `View/onContinueUserActivity(_:perform:)` methods — updates its `preferring` set according to the current selection. The enclosing scene prefers to handle an event for a contact that’s already selected, but doesn’t volunteer itself as a preferred scene when no contact is selected:

```
private struct ContactList: View {
    var store: ContactStore
    @State private var selectedContact: UUID?

    var body: some View {
        NavigationSplitView {
            List(store.contacts, selection: $selectedContact) { contact in
                NavigationLink(contact.name) {
                    Text(contact.name)
                }
            }
        } detail: {
            Text("Select a contact")
        }
        .handlesExternalEvents(
            preferring: selectedContact == nil
                ? []
                : [selectedContact!.uuidString],
            allowing: selectedContact == nil
                ? ["*"]
                : []
        )
        .onContinueUserActivity(Contact.userActivityType) { activity in
            if let identifier = activity.targetContentIdentifier {
                selectedContact = UUID(uuidString: identifier)
            }
        }
        .userActivity(
            Contact.userActivityType,
            isActive: selectedContact != nil
        ) { activity in
            activity.title = "Contact"
            activity.targetContentIdentifier = selectedContact?.uuidString
            activity.isEligibleForHandoff = true
        }
    }
}
```

The above code also updates the `allowing` set to indicate that the scene can handle any incoming event when there’s no current selection, but that it can’t handle any event if the view already displays a contact. The `preferring` set takes precedence in the special case where the incoming event exactly matches the currently selected contact.

