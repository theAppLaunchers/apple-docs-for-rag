

- AppKit
- NSSharingService
- NSSharingService.CloudKitOptions
-  allowPrivate 

Type Property

# allowPrivate

An option that allows the participant to privately distribute the share to other iCloud users.

macOS 10.12+

``` source
static var allowPrivate: NSSharingService.CloudKitOptions { get }
```

## See Also

### CloudKit Options

static var allowPublic: NSSharingService.CloudKitOptions

An option that allows the participant to publicly distribute the share to other iCloud users.

static var allowReadOnly: NSSharingService.CloudKitOptions

An option that allows the participant to grant other participants read-only permissions.

static var allowReadWrite: NSSharingService.CloudKitOptions

An option that allows the participant to grant other participants read-write permissions.

static var standard: NSSharingService.CloudKitOptions

An option that allows the participant to configure the share with a standard set of options.

