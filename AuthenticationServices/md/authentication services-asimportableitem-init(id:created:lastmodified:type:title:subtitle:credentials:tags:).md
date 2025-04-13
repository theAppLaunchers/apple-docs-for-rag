

- Authentication Services
- ASImportableItem
-  init(id:created:lastModified:type:title:subtitle:credentials:tags:) 

Initializer

# init(id:created:lastModified:type:title:subtitle:credentials:tags:)

Creates an importable item.

iOS 18.2+iPadOS 18.2+Mac Catalyst 18.2+macOS 15.2+visionOS 2.2+

``` source
init(
    id: Data,
    created: Date,
    lastModified: Date,
    type: ASImportableItem.ItemType,
    title: String,
    subtitle: String? = nil,
    credentials: [ASImportableCredential],
    tags: [String] = []
)
```

## Parameters 

`id`  

A unique identifier for the item.

`created`  

The item’s creation date and time.

`lastModified`  

The item’s last modified date and time.

`type`  

The type of the item.

`title`  

The user-defined name or title of this Item.

`subtitle`  

A subtitle or description of this item, if any.

`credentials`  

The credentials associated with this item, as an array of ASImportableCredential instances.

`tags`  

The user-defined tags associated with this item, if any.

