

- FSKit
- FSVolume
- FSVolume.Operations
-  renameItem(\_:inDirectory:named:to:inDirectory:overItem:replyHandler:) 

Instance Method

# renameItem(\_:inDirectory:named:to:inDirectory:overItem:replyHandler:)

Renames an item from one path in the file system to another.

macOS 15.4+

``` source
func renameItem(
    _ item: FSItem,
    inDirectory sourceDirectory: FSItem,
    named sourceName: FSFileName,
    to destinationName: FSFileName,
    inDirectory destinationDirectory: FSItem,
    overItem: FSItem?,
    replyHandler reply: @escaping (FSFileName?, (any Error)?) -> Void
)
```

``` source
func renameItem(
    _ item: FSItem,
    inDirectory sourceDirectory: FSItem,
    named sourceName: FSFileName,
    to destinationName: FSFileName,
    inDirectory destinationDirectory: FSItem,
    overItem: FSItem?
) async throws -> FSFileName
```

**Required**

## Parameters 

`item`  

The file system object being renamed.

`sourceDirectory`  

The directory that currently contains the item to rename.

`sourceName`  

The name of the item within the source directory.

`destinationName`  

The new name of the item as it appears in `destinationDirectory`.

`destinationDirectory`  

The directory to contain the renamed object, which may be the same as `sourceDirectory`.

`overItem`  

The file system object if the destination exists, as discovered in a prior lookup. If this parameter is non-`nil`, mark `overItem` as deleted, so the file system can free its allocated space on the next call to reclaimItem(_:replyHandler:). After doing so, ensure the operation finishes without errors.

`reply`  

A block or closure to indicate success or failure. If renaming succeeds, pass the FSFileName as it exists within `destinationDirectory` and a `nil` error. If renaming fails, pass the relevant error as the second parameter; FSKit ignores any FSFileName in this case. For an `async` Swift implementation, there’s no reply handler; simply return the FSFileName or throw an error.

## Discussion

Implement renaming along the lines of this algorithm:

- If `item` is a file:

  - If the destination file exists:

    - Remove the destination file.

  - If the source and destination directories are the same:

    - Rewrite the name in the existing directory.

  - Else:

    - Write the new entry in the destination directory.

    - Clear the old directory entry.

- If `item` is a directory:

  - If the destination directory exists:

    - If the destination directory isn’t empty:

      - Fail the operation with an error of NSPOSIXErrorDomain and a code of `ENOTEMPTY`.

    - Else:

      - Remove the destination directory.

    - If the source and destination directories are the same:

      - Rewrite the name in the existing directory.

    - Else:

      - If the destination is a child of the source directory:

        - Fail the operation with an error.

      - Else:

        - Write the new entry in the destination directory.

        - Update `"."` and `".."` in the moved directory.

        - Clear the old directory entry.

## See Also

### Working with items

func createItem(named: FSFileName, type: FSItem.ItemType, inDirectory: FSItem, attributes: FSItem.SetAttributesRequest, replyHandler: (FSItem?, FSFileName?, (any Error)?) -> Void)

Creates a new file or directory item.

**Required**

class FSFileName

The name of a file, expressed as a data buffer.

enum ItemType

An enumeration of item types, such as file, directory, or symbolic link.

class SetAttributesRequest

A request to set attributes on an item.

func lookupItem(named: FSFileName, inDirectory: FSItem, replyHandler: (FSItem?, FSFileName?, (any Error)?) -> Void)

Looks up an item within a directory.

**Required**

func removeItem(FSItem, named: FSFileName, fromDirectory: FSItem, replyHandler: ((any Error)?) -> Void)

Removes an existing item from a given directory.

**Required**

func reclaimItem(FSItem, replyHandler: ((any Error)?) -> Void)

Reclaims an item, releasing any resources allocated for the item.

**Required**

