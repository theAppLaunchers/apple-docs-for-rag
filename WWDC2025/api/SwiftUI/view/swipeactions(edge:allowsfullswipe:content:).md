*   [SwiftUI](/documentation/swiftui)
*   [View](/documentation/swiftui/view)
*   swipeActions(edge:allowsFullSwipe:content:)

Instance Method

# swipeActions(edge:allowsFullSwipe:content:)

Adds custom swipe actions to a row in a list.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+visionOS 1.0+watchOS 8.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift

```swift
nonisolated
func swipeActions<T>(
    edge: [`HorizontalEdge`](/documentation/swiftui/horizontaledge) = .trailing,
    allowsFullSwipe: [`Bool`](/documentation/Swift/Bool) = true,
    @[`ViewBuilder`](/documentation/swiftui/viewbuilder) content: () -> T
) -> some [`View`](/documentation/swiftui/view) where T : [`View`](/documentation/swiftui/view)
```

```
```
```
```
```
```
```

## [Parameters](/documentation/SwiftUI/View/swipeActions\(edge:allowsFullSwipe:content:\)#parameters)

`edge`

The edge of the view to associate the swipe actions with. The default is [`HorizontalEdge.trailing`](/documentation/swiftui/horizontaledge/trailing).

`allowsFullSwipe`

A Boolean value that indicates whether a full swipe automatically performs the first action. The default is `true`.

`content`

The content of the swipe actions.

## [Discussion](/documentation/SwiftUI/View/swipeActions\(edge:allowsFullSwipe:content:\)#discussion)

Use this method to add swipe actions to a view that acts as a row in a list. Indicate the [`HorizontalEdge`](/documentation/swiftui/horizontaledge) where the swipe action originates, and define individual actions with [`Button`](/documentation/swiftui/button) instances. For example, if you have a list of messages, you can add an action to toggle a message as unread on a swipe from the leading edge, and actions to delete or flag messages on a trailing edge swipe:

```

```
List {
    ForEach(store.messages) { message in
        MessageCell(message: message)
            .swipeActions(edge: .leading) {
                Button { store.toggleUnread(message) } label: {
                    if message.isUnread {
                        Label("Read", systemImage: "envelope.open")
                    } else {
                        Label("Unread", systemImage: "envelope.badge")
                    }
                }
            }
            .swipeActions(edge: .trailing) {
                Button(role: .destructive) {
                    store.delete(message)
                } label: {
                    Label("Delete", systemImage: "trash")
                }
                Button { store.flag(message) } label: {
                    Label("Flag", systemImage: "flag")
                }
            }
        }
    }
}
```

```

Actions appear in the order you list them, starting from the swipe’s originating edge. In the example above, the Delete action appears closest to the screen’s trailing edge:

![A screenshot of a list of messages, where one of the messages has been](https://docs-assets.developer.apple.com/published/262e1f35cb7c1655839ee71ebb1156b7/View-swipeActions-1%402x.png)

For labels or images that appear in swipe actions, SwiftUI automatically applies the [`fill`](/documentation/swiftui/symbolvariants/fill-swift.type.property) symbol variant, as shown above.

By default, the user can perform the first action for a given swipe direction with a full swipe. For the example above, the user can perform both the toggle unread and delete actions with full swipes. You can opt out of this behavior for an edge by setting the `allowsFullSwipe` parameter to `false`. For example, you can disable the full swipe on the leading edge:

```

```
.swipeActions(edge: .leading, allowsFullSwipe: false) {
    Button { store.toggleUnread(message) } label: {
        if message.isUnread {
            Label("Read", systemImage: "envelope.open")
        } else {
            Label("Unread", systemImage: "envelope.badge")
        }
    }
}
```

```

When you set a role for a button using one of the values from the [`ButtonRole`](/documentation/swiftui/buttonrole) enumeration, SwiftUI styles the button according to its role. In the example above, the delete action appears in [`red`](/documentation/swiftui/shapestyle/red) because it has the [`destructive`](/documentation/swiftui/buttonrole/destructive) role. If you want to set a different color — for example, to match the overall theme of your app’s UI — add the [`tint(_:)`](/documentation/swiftui/view/tint\(_:\)) modifier to the button:

```

```
MessageCell(message: message)
    .swipeActions(edge: .leading) {
        Button { store.toggleUnread(message) } label: {
            if message.isUnread {
                Label("Read", systemImage: "envelope.open")
            } else {
                Label("Unread", systemImage: "envelope.badge")
            }
        }
        .tint(.blue)
    }
    .swipeActions(edge: .trailing) {
        Button(role: .destructive) { store.delete(message) } label: {
            Label("Delete", systemImage: "trash")
        }
        Button { store.flag(message) } label: {
            Label("Flag", systemImage: "flag")
        }
        .tint(.orange)
    }
```

```

The modifications in the code above make the toggle unread action [`blue`](/documentation/swiftui/shapestyle/blue) and the flag action [`orange`](/documentation/swiftui/shapestyle/orange):

![A screenshot of a row that the user swiped from the leading edge](https://docs-assets.developer.apple.com/published/3a4c22dfc596282a99c327ad6645eb06/View-swipeActions-2%402x.png)

When you add swipe actions, SwiftUI no longer synthesizes the Delete actions that otherwise appear when using the `ForEach/onDelete(perform:)` method on a [`ForEach`](/documentation/swiftui/foreach) instance. You become responsible for creating a Delete action, if appropriate, among your swipe actions.

Actions accumulate for a given edge if you call the modifier multiple times on the same list row view.

## [See Also](/documentation/SwiftUI/View/swipeActions\(edge:allowsFullSwipe:content:\)#see-also)

### [Configuring interaction](/documentation/SwiftUI/View/swipeActions\(edge:allowsFullSwipe:content:\)#Configuring-interaction)

```swift
```swift
```swift
```swift
func selectionDisabled(Bool) -> some View
```
```

Adds a condition that controls whether users can select this view.
```
```