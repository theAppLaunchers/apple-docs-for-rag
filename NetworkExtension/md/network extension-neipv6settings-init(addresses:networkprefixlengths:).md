

- Network Extension
- NEIPv6Settings
-  init(addresses:networkPrefixLengths:) 

Initializer

# init(addresses:networkPrefixLengths:)

Initializes the IPv6 settings object.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 17.0+visionOS 1.0+

``` source
init(
    addresses: [String],
    networkPrefixLengths: [NSNumber]
)
```

## Parameters 

`addresses`  

An array of IPv6 address strings. These IPv6 addresses will be assigned to the tunnel’s TUN interface.

`networkPrefixLengths`  

An array of IPv6 network prefix lengths. Each prefix length in this array is combined with the IP address in the corresponding index in `addresses` to specify an IPv6 network that the TUN interface is (virtually) connected to. Each prefix length must be set to an integer between 0 and 128.

## Return Value

The initialized `NEIPv6Settings` object.

