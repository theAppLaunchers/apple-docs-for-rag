

- Core Services
- Launch Services
- LSLaunchURLSpec
-  appURL 

Instance Property

# appURL

A Core Foundation URL reference designating the application to launch; see the *CFURL Reference* in the Core Foundation Reference Documentation for a description of the `CFURLRef` data type.The URL must have scheme `file` and contain a valid path to an application file or application bundle. Set this field to `NULL` to request that each item in the `itemURLs` array be opened in its own preferred application.

macOS 10.0+

``` source
var appURL: Unmanaged?
```

## See Also

### Configuring a Launch URL

var asyncRefCon: UnsafeMutableRawPointer?

A pointer to an arbitrary application-defined value, passed in the Carbon event notifying you of an application’s launch or termination (if you have registered for such notification). The value of this field can be `NULL`.

var itemURLs: Unmanaged&lt;CFArray>?

A reference to an array of Core Foundation URL references designating the item or items to open; see the *CFArray Reference* in the Core Foundation Reference Documentation for a description of the `CFArrayRef` data type. The value of this field can be `NULL`, in which case the application designated by `appURL` will be launched without opening any items.

var launchFlags: LSLaunchFlags

Launch flags specifying how to launch each application (including whether to print or merely open documents); see LSLaunchFlags for a description of these flags.

var passThruParams: UnsafePointer&lt;AEDesc>?

A pointer to an Apple event descriptor that is passed untouched as an optional parameter, with keyword `keyAEPropData` (`'prdt'`), in the Apple event sent to each application launched or activated (whether individual preferred applications or the application designated by `appURL`). See the *Apple Event Manager Reference* in the Carbon Interapplication Communication Documentation for a description of the `AEDesc` data type. The value of this field can be `NULL`.

