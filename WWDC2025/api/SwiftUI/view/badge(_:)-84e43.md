*   [SwiftUI](/documentation/swiftui)
*   [View](/documentation/swiftui/view)
*   badge(\_:)

Instance Method

# badge(\_:)

Generates a badge for the view from a localized string key.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+visionOS 1.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift

```swift
nonisolated
func badge(_ key: [`LocalizedStringKey`](/documentation/swiftui/localizedstringkey)?) -> some [`View`](/documentation/swiftui/view)
```

```
```
```
```
```
```
```

```swift
```swift
Show all declarations
```
```

## [Parameters](/documentation/SwiftUI/View/badge\(_:\)-84e43#parameters)

`key`

An optional string key to display as a badge. Set the value to `nil` to hide the badge.

## [Discussion](/documentation/SwiftUI/View/badge\(_:\)-84e43#discussion)

Use a badge to convey optional, supplementary information about a view. Keep the contents of the badge as short as possible. Badges appear in list rows, tab bars, toolbar items, and menus.

This modifier creates a [`Text`](/documentation/swiftui/text) view on your behalf, and treats the localized key similar to [`init(_:tableName:bundle:comment:)`](/documentation/swiftui/text/init\(_:tablename:bundle:comment:\)). For more information about localizing strings, see [`Text`](/documentation/swiftui/text). The following example shows a list with a “Default” badge on one of its rows.

```

```
NavigationView {
    List(servers) { server in
        Text(server.name)
            .badge(server.isDefault ? "Default" : nil)
    }
    .navigationTitle("Servers")
}
```

```

![A table with the navigation title Servers and four rows: North 1,](https://docs-assets.developer.apple.com/published/b5f34f4ffdb5ba98e88b91513e2da519/View-badge-3%402x.png)