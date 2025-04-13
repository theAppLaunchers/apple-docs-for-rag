

- File Provider
-  NSFileProviderDeleteItemOptions 

Structure

# NSFileProviderDeleteItemOptions

Options for deleting items.

iOS 16.0+iPadOS 16.0+macOS 11.0+visionOS 1.0+

``` source
struct NSFileProviderDeleteItemOptions
```

## Topics

### Choosing Delete Options

static var recursive: NSFileProviderDeleteItemOptions

A value indicating that the delete operation removes the item and all of its children.

### Creating Delete Options

init(rawValue: UInt)

Creates an option instance from the raw value.

## Relationships

### Conforms To

- BitwiseCopyable
- Equatable
- ExpressibleByArrayLiteral
- OptionSet
- RawRepresentable
- Sendable
- SetAlgebra

## See Also

### Managing Items

func createItem(basedOn: NSFileProviderItem, fields: NSFileProviderItemFields, contents: URL?, options: NSFileProviderCreateItemOptions, request: NSFileProviderRequest, completionHandler: (NSFileProviderItem?, NSFileProviderItemFields, Bool, (any Error)?) -> Void) -> Progress

Tells the file provider to create or import an item based on a template.

**Required**

struct NSFileProviderCreateItemOptions

Options for creating items.

func modifyItem(NSFileProviderItem, baseVersion: NSFileProviderItemVersion, changedFields: NSFileProviderItemFields, contents: URL?, options: NSFileProviderModifyItemOptions, request: NSFileProviderRequest, completionHandler: (NSFileProviderItem?, NSFileProviderItemFields, Bool, (any Error)?) -> Void) -> Progress

Tells the file provider that an item’s content or metadata changed.

**Required**

struct NSFileProviderModifyItemOptions

Options for modifying items.

func deleteItem(identifier: NSFileProviderItemIdentifier, baseVersion: NSFileProviderItemVersion, options: NSFileProviderDeleteItemOptions, request: NSFileProviderRequest, completionHandler: ((any Error)?) -> Void) -> Progress

Tells the file provider to delete an item forever.

**Required**

