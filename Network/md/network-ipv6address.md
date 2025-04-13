

- Network
-  IPv6Address 

Structure

# IPv6Address

A structure containing an IPv6 address.

iOS 12.0+iPadOS 12.0+Mac Catalyst 12.0+macOS 10.14+tvOS 12.0+visionOS 1.0+watchOS 5.0+

``` source
struct IPv6Address
```

## Topics

### Creating Addresses

init?(String)

Initializes an IPv6 address with a string.

init?(Data, NWInterface?)

Initializes an IPv6 address with data.

var asIPv4: IPv4Address?

Extracts the IPv4 address contained within the IPv6 address, if the IPv6 address is an IPv4-mapped or IPv4-compatible address.

### Inspecting Address Properties

var rawValue: Data

The raw data of an IPv6 address.

let interface: NWInterface?

The IPv6 scoped interface associated with this address.

var multicastScope: IPv6Address.Scope?

The IPv6 multicast scope of the address.

enum Scope

An IPv6 multicast scope.

var isAny: Bool

A Boolean indicating whether the address is the unspecified address (::).

var is6to4: Bool

A Boolean indicating whether the address is a 6to4 address.

var isIPv4Compatabile: Bool

A Boolean indicating whether the address is IPv4-compatible.

var isIPv4Mapped: Bool

A Boolean indicating whether the address is an IPv4-mapped address.

var isLinkLocal: Bool

A Boolean indicating whether this address is in a link-local range.

var isLoopback: Bool

A Boolean indicating whether this address is a loopback address for the local device.

var isMulticast: Bool

A Boolean indicating whether this address is a multicast address.

### Setting Well-Known Addresses

static let any: IPv6Address

The unspecified address (::).

static let broadcast: IPv6Address

The unspecified broadcast address (::).

static let loopback: IPv6Address

The device’s loopback address (::1).

static let nodeLocalNodes: IPv6Address

The multicast address for all local nodes (ff01::1).

static let linkLocalNodes: IPv6Address

The multicast address for all link-local nodes (ff02::1).

static let linkLocalRouters: IPv6Address

The multicast address for all link-local routers (ff02::2).

### Instance Properties

var isUniqueLocal: Bool

## Relationships

### Conforms To

- CustomDebugStringConvertible
- Equatable
- Hashable
- IPAddress
- Sendable

## See Also

### Internet Addresses

protocol IPAddress

An abstract protocol you use to interact with IP addresses.

struct IPv4Address

A structure containing an IPv4 address.

