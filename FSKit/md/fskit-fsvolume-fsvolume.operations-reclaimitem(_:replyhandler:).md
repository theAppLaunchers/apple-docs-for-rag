

- FSKit
- FSVolume
- FSVolume.Operations
-  reclaimItem(\_:replyHandler:) 

Instance Method

# reclaimItem(\_:replyHandler:)

Reclaims an item, releasing any resources allocated for the item.

macOS 15.4+

``` source
func reclaimItem(
    _ item: FSItem,
    replyHandler reply: @escaping ((any Error)?) -> Void
)
```

``` source
func reclaimItem(_ item: FSItem) async throws
```

**Required**

## Parameters 

`item`  

The item to reclaim.

`reply`  

A block or closure to indicate success or failure. If removal fails, pass an error as the one parameter to the reply handler. If removal succeeds, pass `nil`. For an `async` Swift implementation, there’s no reply handler; simply throw an error or return normally.

## Discussion

FSKit guarantees that for every FSItem returned by the volume, a corresponding reclaim operation occurs after the upper layers no longer reference that item.

Note

Block device file systems may assess whether an underyling resource terminates before processing reclaim operations. On unary file systems, for example, the associated volumes unmount when such resources disconnect from the system. The unmount triggers a reclaiming of all items. Some implementations benefit greatly from short-circuiting in such cases. With a terminated resource, all I/O results in an error, making short-circuiting the most efficient response.

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

func renameItem(FSItem, inDirectory: FSItem, named: FSFileName, to: FSFileName, inDirectory: FSItem, overItem: FSItem?, replyHandler: (FSFileName?, (any Error)?) -> Void)

Renames an item from one path in the file system to another.

**Required**

