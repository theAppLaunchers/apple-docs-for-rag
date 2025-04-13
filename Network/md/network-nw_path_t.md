

- Network
-  nw_path_t 

Type Alias

# nw_path_t

An object that contains information about the properties of the network that a connection uses, or that are available to your app.

iOS 12.0+iPadOS 12.0+Mac Catalyst 13.0+macOS 10.14+tvOS 12.0+visionOS 1.0+watchOS 6.0+

``` source
typealias nw_path_t = any OS_nw_path
```

## Topics

### Checking Path Availability

func nw_path_get_status(nw_path_t) -> nw_path_status_t

Checks whether a path can be used by connections.

struct nw_path_status_t

Status values indicating whether a path can be used by connections.

### Inspecting Interfaces

func nw_path_uses_interface_type(nw_path_t, nw_interface_type_t) -> Bool

Checks if connections using the path may send traffic over a specific interface type.

func nw_path_enumerate_interfaces(nw_path_t, (nw_interface_t) -> Bool)

Enumerates the list of all interfaces available to the path, in order of preference.

typealias nw_path_enumerate_interfaces_block_t

A block that enumerates the interfaces available to a path.

func nw_path_enumerate_gateways(nw_path_t, (nw_endpoint_t) -> Bool)

Enumerates the list of gateways configured on the interfaces available to a path.

typealias nw_path_enumerate_gateways_block_t

A block that enumerates the gateways configured on the interfaces available to a path.

### Checking Path Capabilities

func nw_path_has_ipv4(nw_path_t) -> Bool

Checks whether the path can route IPv4 traffic.

func nw_path_has_ipv6(nw_path_t) -> Bool

Checks whether the path can route IPv6 traffic.

func nw_path_has_dns(nw_path_t) -> Bool

Checks whether the path has a DNS server configured.

func nw_path_is_constrained(nw_path_t) -> Bool

Checks whether the path uses an interface in Low Data Mode.

func nw_path_is_expensive(nw_path_t) -> Bool

Checks whether the path uses an interface that is considered expensive, such as Cellular or a Personal Hotspot.

### Comparing Paths

func nw_path_is_equal(nw_path_t, nw_path_t) -> Bool

Compares if two paths are identical.

### Inspecting Connected Paths

func nw_path_copy_effective_local_endpoint(nw_path_t) -> nw_endpoint_t?

Accesses the local endpoint in use by a connection’s network path.

func nw_path_copy_effective_remote_endpoint(nw_path_t) -> nw_endpoint_t?

Accesses the remote endpoint in use by a connection’s network path.

