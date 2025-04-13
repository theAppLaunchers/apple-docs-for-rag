

- System
- FilePermissions
-  setGroupID 

Type Property

# setGroupID

Indicates that the file is executed as the group.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 14.0+visionOS 1.0+watchOS 7.0+

``` source
static var setGroupID: FilePermissions { get }
```

## Discussion

For more information, see the `setgid(2)` man page.

## See Also

### Special Permissions

static var setUserID: FilePermissions

Indicates that the file is executed as the owner.

static var saveText: FilePermissions

Indicates that executable’s text segment should be kept in swap space even after it exits.

