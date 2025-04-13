

- App Intents
- IntentItem
-  init(\_:title:subtitle:image:) 

Initializer

# init(\_:title:subtitle:image:)

Creates an item with the specified value and visual attributes.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
init(
    _ value: Value,
    title: LocalizedStringResource,
    subtitle: LocalizedStringResource? = nil,
    image: DisplayRepresentation.Image? = nil
)
```

## Parameters 

`value`  

The value the item represents.

`title`  

The item’s title.

`subtitle`  

The item’s subtitle.

`image`  

An image to display alongside the item’s title.

## Discussion

Note

The system uses the provided values even when `value` conforms to the DisplayRepresentable protocol.

