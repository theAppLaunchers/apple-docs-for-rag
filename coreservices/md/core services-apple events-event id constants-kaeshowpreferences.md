

- Core Services
- Apple Events
- Event ID Constants
-  kAEShowPreferences 

Global Variable

# kAEShowPreferences

Mac Catalyst 13.0+macOS 10.0+

``` source
var kAEShowPreferences: AEEventID { get }
```

## Discussion

Event sent by the macOS to a process when the user chooses the Preferences item for that process.

Carbon applications that handle the Preferences command can install an Apple event handler for this event, but they more commonly install a Carbon event handler for `kEventCommandProcess` and check for the `kHICommandPreferences` command ID.

