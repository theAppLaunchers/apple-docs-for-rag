

- TV Services
-  TVTopShelfItem 

Class

# TVTopShelfItem

An item that uses an image to represent a movie, show, or other content in the top shelf.

tvOS 13.0+

``` source
class TVTopShelfItem
```

## Overview

A TVTopShelfItem object manages basic traits for all items, including the images they display and the actions they trigger. Typically, you create TVTopShelfCarouselItem or TVTopShelfSectionedItem objects for your interface. For inset interfaces, you can also create TVTopShelfItem objects directly.

After creating an item object, assign an image and one or more actions to it, and update any other relevant properties. Return the item object as part of the content for your interface.

Each unique item in your app must have a correspondingly unique identifier, and the identifier for each item must remain stable throughout the life of your app. Do not assign a different unique identifier for the same underlying item each time you create a TVTopShelfItem object for it.

## Topics

### Creating a Top Shelf Item

init(identifier: String)

Creates a top shelf item with the specified identifier.

### Assigning Actions to the Item

var playAction: TVTopShelfAction?

The action to perform when the user wants to play the current item.

var displayAction: TVTopShelfAction?

The action to perform when the user wants to see more information for the current item.

### Providing an Image for the Item

func imageURL(for: TVTopShelfItem.ImageTraits) -> URL?

Returns an image associated with the current item.

func setImageURL(URL?, for: TVTopShelfItem.ImageTraits)

Associates an image with the current item.

struct ImageTraits

Constants describing the image format.

### Getting the Item Attributes

var identifier: String

The unique identifier for the item.

var expirationDate: Date?

The date on which the item becomes unavailable.

## Relationships

### Inherits From

- TVTopShelfObject

### Inherited By

- TVTopShelfCarouselItem
- TVTopShelfSectionedItem

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSObjectProtocol

## See Also

### Common types

class TVTopShelfAction

An action to perform in response to user interactions with an item in the top shelf.

protocol TVTopShelfContent

The protocol that objects adopt to provide content for the top shelf.

class TVTopShelfObject

An abstract base class for describing top shelf items and item collections.

