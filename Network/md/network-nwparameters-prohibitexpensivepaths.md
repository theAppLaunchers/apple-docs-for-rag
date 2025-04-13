

- Network
- NWParameters
-  prohibitExpensivePaths 

Instance Property

# prohibitExpensivePaths

A Boolean that prevents connections, listeners, and browsers from using network paths marked as expensive.

iOS 12.0+iPadOS 12.0+Mac Catalyst 12.0+macOS 10.14+tvOS 12.0+visionOS 1.0+watchOS 5.0+

``` source
final var prohibitExpensivePaths: Bool { get set }
```

## Discussion

To test the behavior of this property, you can override the device’s current values for cellular and Wi-Fi cost in Settings \> Developer \> Network Override.

Tip

Prefer basing your app’s policy logic around the prohibitConstrainedPaths property rather than this one. People using your app can use the “Low Data Mode” setting to set the constrained status, and thereby choose to use a potentially expensive network.

## See Also

### Selecting Paths

var requiredInterfaceType: NWInterface.InterfaceType

An interface type to require on connections and listeners.

var requiredInterface: NWInterface?

A specific interface to require on connections, listeners, and browsers.

var requiredLocalEndpoint: NWEndpoint?

A specific local IP address and port to use for connections and listeners.

var prohibitConstrainedPaths: Bool

A Boolean that prevents connections, listeners, and browsers from using network paths marked as constrained by Low Data Mode.

var prohibitedInterfaceTypes: [NWInterface.InterfaceType]?

A list of interface types that connections, listeners, and browsers will not use.

var prohibitedInterfaces: [NWInterface]?

A list of specific interfaces that connections and listeners will not use.

