

- UIKit
-  UINib 

Class

# UINib

An object that contains Interface Builder nib files.

iOS 4.0+iPadOS 4.0+Mac Catalyst 13.1+tvOSvisionOS 1.0–1.0Deprecated

``` source
@MainActor
class UINib
```

## Overview

A UINib object caches the contents of a nib file in memory, ready for unarchiving and instantiation. When your app needs to instantiate the contents of the nib file, it can do so without having to load the data from the nib file first, which improves performance. The UINib object can automatically release this cached nib data to free up memory for your app under low-memory conditions, reloading that data the next time your app instantiates the nib.

Your app should use UINib objects whenever it needs to repeatedly instantiate the same nib data. For example, if your table view uses a nib file to instantiate table view cells, caching the nib in a UINib object can improve performance.

When you create a UINib object using the contents of a nib file, the object loads the object graph in the referenced nib file, but it doesn’t unarchive it yet. To unarchive all of the nib data and instantiate the nib, your app calls the instantiate(withOwner:options:) method. For more information about the steps that the UINib object follows to instantiate the nib’s object graph, see Resource Programming Guide.

## Topics

### Creating a nib object

init(nibName: String, bundle: Bundle?)

Returns a nib object from the nib file in the specified bundle.

init(data: Data, bundle: Bundle?)

Creates a nib object from nib data stored in memory.

### Retrieving objects from the nib file

func instantiate(withOwner: Any?, options: [UINib.OptionsKey : Any]?) -> [Any]

Unarchives and instantiates the in-memory contents of the nib object’s nib file, creating a distinct object tree and set of top-level objects.

struct OptionsKey

Options that specify how to unarchive and instantiate the nib.

## Relationships

### Inherits From

- NSObject

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSObjectProtocol
- Sendable

