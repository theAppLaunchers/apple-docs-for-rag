

- Network Extension
-  NEAppProxyProvider 

Class

# NEAppProxyProvider

The principal class for an app proxy provider app extension.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+visionOS 1.0+

``` source
class NEAppProxyProvider
```

## Mentioned in 

Handling Flow Copying

## Overview

The NEAppProxyProvider class provides access to flows of network data in the form of NEAppProxyFlow objects. Each NEAppProxyFlow object corresponds to a socket opened by an app that matches the app rules specified in the current App Proxy configuration. Your App Proxy Provider acts as a transparent network proxy for the flows of network data that it receives.

Important

The `com.apple.developer.networking.networkextension` entitlement is required to use the NEAppProxyProvider class. Enable this entitlement when creating an App ID in your developer account.

### DNS Handling

In addition to flows of raw network data from applications, the App Proxy Provider also receives flows of DNS queries in the form of NEAppProxyUDPFlow objects. DNS query flows are received only for applications that use low-level DNS resolution APIs such as DNSServiceGetAddrInfo(_:_:_:_:_:_:_:)(). The App Proxy Provider can specify the DNS resolver configuration that will be used by these applications using the setTunnelNetworkSettings(_:completionHandler:) method.

Applications that use higher-level networking APIs such as URLSession and NSURLConnection do not generate DNS queries. Instead the destination hostname for the connection is included in the endpoint information of the NEAppProxyFlow object.

### Creating an App Proxy Provider Extension

App Proxy Providers run as App Extensions for the `com.apple.networkextension.app-proxy` extension point.

To create a App Proxy Provider extension, first create a new App Extension target in your project.

For an example of an Xcode build target for this app extension, see the SimpleTunnel: Customized Networking Using the NetworkExtension Framework sample code project.

Once you have a App Proxy Provider extension target, create a sub-class of `NEAppProxyProvider`. Then, set the `NSExtensionPrincipalClass` key in the the extension’s `Info.plist` to the name of your sub-class.

If it is not already done, set the `NSExtensionPointIdentifier` key in the extension’s `Info.plist` to `com.apple.networkextension.app-proxy`.

Here is an example of the NSExtension dictionary in a App Proxy Provider extension’s `Info.plist`:

```
```

Finally, add your App Proxy Provider extension target to your app’s Embed App Extensions build phase.

### Subclassing Notes

In order to create a App Proxy Provider extension, you must create a subclass of `NEAppProxyProvider` and override the methods listed below.

#### Methods to Override

- startProxy(options:completionHandler:)

- stopProxy(with:completionHandler:)

- handleNewFlow(_:)

## Topics

### Managing the app proxy life cycle

func startProxy(options: [String : Any]?, completionHandler: ((any Error)?) -> Void)

Start the network proxy.

func stopProxy(with: NEProviderStopReason, completionHandler: () -> Void)

Stop the network proxy.

func cancelProxyWithError((any Error)?)

Stop the network proxy from the App Proxy Provider.

### Handling proxied flows

func handleNewFlow(NEAppProxyFlow) -> Bool

Handle a new flow of network data.

func handleNewUDPFlow(NEAppProxyUDPFlow, initialRemoteEndpoint: NWEndpoint) -> Bool

Handle a new UDP flow of network data.

Deprecated

## Relationships

### Inherits From

- NETunnelProvider

### Inherited By

- NETransparentProxyProvider

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSObjectProtocol

## See Also

### App proxy provider

class NETunnelProvider

An abstract base class shared by NEPacketTunnelProvider and NEAppProxyProvider.

class NEProvider

An abstract base class for all NetworkExtension providers.

class NETunnelNetworkSettings

The configuration for a tunnel provider’s virtual interface.

