

- Network Extension
-  NEProxySettings 

Class

# NEProxySettings

`NEProxySettings` contains HTTP proxy settings.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 17.0+visionOS 1.0+

``` source
class NEProxySettings
```

## Overview

`NEProxySettings` is used in the context of a VPN configuration to specify the proxy that should be used for network traffic when the VPN is active.

Instances of this class are thread safe.

## Topics

### Accessing Automatic Proxy Properties

var autoProxyConfigurationEnabled: Bool

A Boolean indicating if proxy auto-configuration is enabled.

var proxyAutoConfigurationURL: URL?

A URL specifying the location from where the Proxy Auto Configuration (PAC) script should be downloaded.

var proxyAutoConfigurationJavaScript: String?

A string containing the Proxy Auto Configuration (PAC) JavaScript source code.

### Accessing Manual Proxy Properties

var httpEnabled: Bool

A Boolean indicating if a static HTTP proxy will be used.

var httpServer: NEProxyServer?

An NEProxyServer object containing the static HTTP proxy server settings.

var httpsEnabled: Bool

A Boolean indicating if a static HTTPS proxy will be used.

var httpsServer: NEProxyServer?

An NEProxyServer object containing the static HTTPS proxy server settings.

class NEProxyServer

`NEProxyServer` contains settings for a proxy server.

### Accessing General Proxy Properties

var excludeSimpleHostnames: Bool

A Boolean indicating if HTTP requests using single-label host names should be excluded from using the proxy settings.

var exceptionList: [String]?

An array of domain name patterns. If the destination host name of an HTTP connection matches one of these patterns then the proxy settings will not be used for the connection.

var matchDomains: [String]?

An array of domain strings.

## Relationships

### Inherits From

- NSObject

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSCoding
- NSCopying
- NSObjectProtocol
- NSSecureCoding

## See Also

### Accessing tunnel network settings

var tunnelRemoteAddress: String

The IP address of the tunnel server.

var dnsSettings: NEDNSSettings?

The tunnel DNS settings.

class NEDNSSettings

The DNS resolver settings of a network tunnel or a system-wide configuration.

var proxySettings: NEProxySettings?

The tunnel HTTP proxy settings.

