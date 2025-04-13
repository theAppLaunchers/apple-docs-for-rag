

- Network
- NWParameters
-  requiredLocalEndpoint 

Instance Property

# requiredLocalEndpoint

A specific local IP address and port to use for connections and listeners.

iOS 12.0+iPadOS 12.0+Mac Catalyst 12.0+macOS 10.14+tvOS 12.0+visionOS 1.0+watchOS 5.0+

``` source
final var requiredLocalEndpoint: NWEndpoint? { get set }
```

## See Also

### Selecting Paths

var requiredInterfaceType: NWInterface.InterfaceType

An interface type to require on connections and listeners.

var requiredInterface: NWInterface?

A specific interface to require on connections, listeners, and browsers.

var prohibitConstrainedPaths: Bool

A Boolean that prevents connections, listeners, and browsers from using network paths marked as constrained by Low Data Mode.

var prohibitExpensivePaths: Bool

A Boolean that prevents connections, listeners, and browsers from using network paths marked as expensive.

var prohibitedInterfaceTypes: [NWInterface.InterfaceType]?

A list of interface types that connections, listeners, and browsers will not use.

var prohibitedInterfaces: [NWInterface]?

A list of specific interfaces that connections and listeners will not use.

