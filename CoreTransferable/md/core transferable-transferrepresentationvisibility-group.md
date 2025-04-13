

- Core Transferable
- TransferRepresentationVisibility
-  group 

Type Property

# group

The visibility level that specifies that the item is visible only to macOS apps in the same App Group.

macOS 13.0+

``` source
static let group: TransferRepresentationVisibility
```

## See Also

### Specifying transfer visibility

static let all: TransferRepresentationVisibility

The visibility level that specifies that any app or process can access the item.

static let team: TransferRepresentationVisibility

The visibility level that specifies that the item is visible only to apps created by the current app’s development team.

static let ownProcess: TransferRepresentationVisibility

The visibility level that specifies that the item is visible only within the app that’s the source of the item.

