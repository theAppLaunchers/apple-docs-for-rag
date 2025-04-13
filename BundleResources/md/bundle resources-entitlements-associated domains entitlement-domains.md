

- Bundle Resources
- Entitlements
-  Associated Domains Entitlement 

Property List Key

# Associated Domains Entitlement

The associated domains for specific services, such as shared web credentials, universal links, and App Clips.

iOS 9.0+iPadOS 9.0+macOS 10.15+tvOS 9.0+visionOS 1.0+watchOS 6.0+

## Details 

Key  
com.apple.developer.associated-domains

Type  

array of strings

## Discussion

This key specifies a list of domains for each enabled service. Add an associated domain to the list in the following format:

```
```

Services include:

`webcredentials`  
Use this service for shared web credentials.

`applinks`  
Use this service for universal links.

`activitycontinuation`  
Use this service for Handoff.

`appclips`  
Use this service for an App Clip.

Note

In macOS 11 and later and iOS 14 and later, apps request `apple-app-site-association` files from an Apple-managed content delivery network (CDN) specifically for associated domains, instead of directly from your web server. If the CDN has an old version of the file, or doesn’t already have a copy of the file, it connects to your web server to obtain the latest version.

If you use a private web server, which is unreachable from the public internet, while developing your app, enable the alternate mode feature to bypass the CDN and connect directly to your server. To do this, add a query string to your associated domains entitlement, as shown in the following example:

```
```

Where `alternate mode` is one of the following:

`developer`  
Specifies that only devices in developer mode can access the domain. In this mode, you can use any valid SSL certificate on your web server, including a certificate that the system doesn’t trust. Make sure you don’t expose your users to security issues, such as machine-in-the-middle attacks. As an additional precaution, only apps that you sign with a development profile can use developer mode, and users must opt-in on any device they use.

`managed`  
Specifies that only devices using a mobile device management (MDM) profile can access the domain. This mode requires consent from the MDM administrator.

`developer+managed`  
Specifies that only devices that are in both `developer` and `managed` modes can access the domain.

To enable associated domains, add the Associated Domains capability to your target in Xcode. For more information, see Adding capabilities to your app.

Important

For watchOS apps, you must add the Associated Domains capability to the WatchKit Extension target.

## See Also

### Related Documentation

Supporting associated domains

Connect your app and a website to provide both a native app and a browser experience.

Creating an App Clip with Xcode

Add an App Clip target to your Xcode project and share code between the App Clip and its corresponding full app.

### Networking

Network Extensions Entitlement

The APIs an app can use to customize networking features.

**Key:** com.apple.developer.networking.networkextension

Personal VPN Entitlement

The API an app can use to create and control a custom system VPN configuration.

**Key:** com.apple.developer.networking.vpn.api

com.apple.developer.networking.multicast

A Boolean value that indicates whether an app can send or receive IP multicast traffic.

com.apple.developer.associated-domains.applinks.read-write

A Boolean value that indicates whether the app can use universal links.

com.apple.developer.networking.manage-thread-network-credentials

A Boolean value that indicates whether the app can use ThreadNetwork.

5G Network Slicing App Category

The key that defines the app category entitlement to enable Cellular Network Slicing.

**Key:** com.apple.developer.networking.slicing.appcategory

5G Network Slicing Traffic Category

The key that defines the traffic category entitlement to enable Cellular Network Slicing.

**Key:** com.apple.developer.networking.slicing.trafficcategory

com.apple.developer.networking.vmnet

