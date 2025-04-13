

- Foundation
- URLProtectionSpace
-  init(host:port:protocol:realm:authenticationMethod:) 

Initializer

# init(host:port:protocol:realm:authenticationMethod:)

Creates a protection space object from the given host, port, protocol, realm, and authentication method.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.1+macOS 10.2+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
init(
    host: String,
    port: Int,
    protocol: String?,
    realm: String?,
    authenticationMethod: String?
)
```

## Parameters 

`host`  

The host name for the URLProtectionSpace object.

`port`  

The port for the protection space object. If `port` is 0, the default port for the specified protocol is used, for example, port 80 for HTTP. Note that servers can, and do, treat these values differently.

`protocol`  

The protocol for the protection space object. The value of `protocol` is equivalent to the scheme for a URL in the protection space, for example, “http”, “https”, “ftp”, etc.

`realm`  

A string indicating a protocol-specific subdivision of the host. `realm` may be `nil` if there is no specified realm or if the protocol doesn’t support realms.

`authenticationMethod`  

The type of authentication to use. `authenticationMethod` should be set to one of the values in NSURLProtectionSpace authentication method constants or `nil` to use the default, NSURLAuthenticationMethodDefault.

## Return Value

A new protection space object, initialized with the given host, port, protocol, realm, and authentication method.

## See Also

### Creating a protection space

init(proxyHost: String, port: Int, type: String?, realm: String?, authenticationMethod: String?)

Creates a protection space object representing a proxy server.

