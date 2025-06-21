*   [AppKit](/documentation/appkit)
*   NSPreviewRepresentableActivityItem

Protocol

# NSPreviewRepresentableActivityItem

An interface you adopt in custom objects that you want to share using the macOS share sheet.

macOS 13.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
protocol NSPreviewRepresentableActivityItem : [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)
```
```
```
```
```
```
```
```

## [Overview](/documentation/AppKit/NSPreviewRepresentableActivityItem#overview)

Adopt the [`NSPreviewRepresentableActivityItem`](/documentation/appkit/nspreviewrepresentableactivityitem) interface in custom types your app makes available for sharing. Use this protocol to specify the item itself and a title and image the share sheet can use to create a preview for your item. To share the item from your app, initialize the [`NSSharingServicePicker`](/documentation/appkit/nssharingservicepicker) object with the object that adopts this protocol.

Note

If your data consists of standard types like strings or images, use an [`NSPreviewRepresentingActivityItem`](/documentation/appkit/nspreviewrepresentingactivityitem) object to specify metadata for those types. If your data consists of URLs, pass them directly to the sharing service picker instead of creating a custom preview item.

## [Topics](/documentation/AppKit/NSPreviewRepresentableActivityItem#topics)

### [Providing the Item to Share](/documentation/AppKit/NSPreviewRepresentableActivityItem#Providing-the-Item-to-Share)

```swift
```swift
```swift
```swift
var item: Any
```
```

The app-specific item you want to share.

**Required**
```
```

### [Providing Metadata About the Item](/documentation/AppKit/NSPreviewRepresentableActivityItem#Providing-Metadata-About-the-Item)

```swift
```swift
```swift
```swift
var title: String?
```
```

A localized string that contains the name of the item.
```
```swift
```swift
```swift
var imageProvider: NSItemProvider?
```
```

An object that provides a visual representation of the item.
```
```swift
```swift
```swift
var iconProvider: NSItemProvider?
```
```

An object that provides an icon that represents the item’s source.
```
```

## [Relationships](/documentation/AppKit/NSPreviewRepresentableActivityItem#relationships)

### [Inherits From](/documentation/AppKit/NSPreviewRepresentableActivityItem#inherits-from)

*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)

### [Conforming Types](/documentation/AppKit/NSPreviewRepresentableActivityItem#conforming-types)

*   [`NSPreviewRepresentingActivityItem`](/documentation/appkit/nspreviewrepresentingactivityitem)

## [See Also](/documentation/AppKit/NSPreviewRepresentableActivityItem#see-also)

### [App Services](/documentation/AppKit/NSPreviewRepresentableActivityItem#App-Services)

```swift
```swift
```swift
```swift
class NSSharingService
```
```

An object that facilitates the sharing of content with social media services, or with apps like Mail or Safari.
```
```swift
```swift
```swift
class NSSharingServicePicker
```
```

A list of sharing services that the user can choose from.
```
```swift
```swift
```swift
class NSSharingServicePickerToolbarItem
```
```

A toolbar item that displays the macOS share sheet.
```
```swift
```swift
```swift
protocol NSServicesMenuRequestor
```
```

A set of methods that support interaction with items users can share through a sharing service.
```
```swift
```swift
```swift
protocol NSCloudSharingServiceDelegate
```
```

A set of methods for responding to the life cycle events of the cloud-sharing service.
```

[

API Reference

Services Functions](/documentation/appkit/services-functions)

Configure the contents of your app’s Services menu.
```