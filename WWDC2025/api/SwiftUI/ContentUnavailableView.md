*   [SwiftUI](/documentation/swiftui)
*   ContentUnavailableView

Structure

# ContentUnavailableView

An interface, consisting of a label and additional content, that you display when the content of your app is unavailable to users.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
struct ContentUnavailableView<Label, Description, Actions> where Label : [`View`](/documentation/swiftui/view), Description : [`View`](/documentation/swiftui/view), Actions : [`View`](/documentation/swiftui/view)
```
```
```
```
```
```
```
```

## [Overview](/documentation/SwiftUI/ContentUnavailableView#overview)

It is recommended to use `ContentUnavailableView` in situations where a view’s content cannot be displayed. That could be caused by a network error, a list without items, a search that returns no results etc.

You create an `ContentUnavailableView` in its simplest form, by providing a label and some additional content such as a description or a call to action:

```

```
ContentUnavailableView {
    Label("No Mail", systemImage: "tray.fill")
} description: {
    Text("New mails you receive will appear here.")
}
```

```

The system provides default `ContentUnavailableView`s that you can use in specific situations. The example below illustrates the usage of the [`search`](/documentation/swiftui/contentunavailableview/search) view:

```swift
```swift
```swift
```swift
```swift
```swift
struct ContentView: View {
```
```
    @ObservedObject private var viewModel = ContactsViewModel()
    var body: some View {
        NavigationStack {
            List {
                ForEach(viewModel.searchResults) { contact in
                    NavigationLink {
                        ContactsView(contact)
                    } label: {
                        Text(contact.name)
                    }
                }
            }
            .navigationTitle("Contacts")
            .searchable(text: $viewModel.searchText)
            .overlay {
                if searchResults.isEmpty {
                    ContentUnavailableView.search
                }
            }
        }
    }
}
```
```
```
```

## [Topics](/documentation/SwiftUI/ContentUnavailableView#topics)

### [Getting built-in unavailable views](/documentation/SwiftUI/ContentUnavailableView#Getting-built-in-unavailable-views)

[`static var search: ContentUnavailableView<SearchUnavailableContent.Label, SearchUnavailableContent.Description, SearchUnavailableContent.Actions>`](/documentation/swiftui/contentunavailableview/search)

Creates a `ContentUnavailableView` instance that conveys a search state.

[`static func search(text: String) -> ContentUnavailableView<Label, Description, Actions>`](/documentation/swiftui/contentunavailableview/search\(text:\))

Creates a `ContentUnavailableView` instance that conveys a search state.

### [Creating an unavailable view](/documentation/SwiftUI/ContentUnavailableView#Creating-an-unavailable-view)

[`init(label: () -> Label, description: () -> Description, actions: () -> Actions)`](/documentation/swiftui/contentunavailableview/init\(label:description:actions:\))

Creates an interface, consisting of a label and additional content, that you display when the content of your app is unavailable to users.

[`init(_:image:description:)`](/documentation/swiftui/contentunavailableview/init\(_:image:description:\))

Creates an interface, consisting of a title generated from a localized string, an image and additional content, that you display when the content of your app is unavailable to users.

[`init(_:systemImage:description:)`](/documentation/swiftui/contentunavailableview/init\(_:systemimage:description:\))

Creates an interface, consisting of a title generated from a localized string, a system icon image and additional content, that you display when the content of your app is unavailable to users.

### [Supporting types](/documentation/SwiftUI/ContentUnavailableView#Supporting-types)

```swift
```swift
```swift
```swift
struct SearchUnavailableContent
```
```

A structure that represents the body of a static placeholder search view.
```
```

## [Relationships](/documentation/SwiftUI/ContentUnavailableView#relationships)

### [Conforms To](/documentation/SwiftUI/ContentUnavailableView#conforms-to)

*   [`View`](/documentation/swiftui/view)