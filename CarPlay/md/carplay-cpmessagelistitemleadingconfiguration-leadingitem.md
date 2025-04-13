

- CarPlay
- CPMessageListItemLeadingConfiguration
-  leadingItem 

Instance Property

# leadingItem

The configuration’s item.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+

``` source
var leadingItem: CPMessageLeadingItem { get }
```

## Discussion

Configurations are immutable. To change or remove the item that the message list item’s leading region shows, create a new configuration and update the list item’s leadingConfiguration property.

## See Also

### Getting the Leading Item

enum CPMessageLeadingItem

The accessories that a message list item can display in its leading region.

