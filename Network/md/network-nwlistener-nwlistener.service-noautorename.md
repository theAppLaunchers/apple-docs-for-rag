

- Network
- NWListener
- NWListener.Service
-  noAutoRename 

Instance Property

# noAutoRename

A Boolean that indicates whether the service prohibits automatic renaming in the event of a name conflict.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
var noAutoRename: Bool { get set }
```

## See Also

### Defining Services

init(name: String?, type: String, domain: String?, txtRecord: Data?)

Initializes a Bonjour service to advertise.

init(name: String?, type: String, domain: String?, txtRecord: NWTXTRecord)

Initializes a Bonjour service to advertise with a TXT record.

