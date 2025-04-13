

- tvOS Release Notes
-  tvOS 12 Release Notes 

Article

# tvOS 12 Release Notes

Update your apps to use new features, and test your apps against API changes.

## Overview

The tvOS 12 SDK provides support for developing tvOS apps for Apple TV devices running tvOS 12. For information about new features in tvOS 12, see What’s New in tvOS. The SDK comes bundled with Xcode 10 available from the Mac App Store. For information about Xcode 10, see Xcode 10 Release Notes.

### Dolby Atmos

#### New Features

- Some iTunes Store movies are now available with Dolby Atmos. If you encounter any issues when playing Atmos-capable titles, file a bug that includes a sysdiagnose and a detailed description of your development hardware configuration.

### Network-Based Device Pairing

#### Known Issues

- PIN pairing with a remote Apple TV might not successfully establish the connection on the first attempt. (40228498)

  **Workaround:** Exit and reenter the Remotes and Devices pairing screen on Apple TV, then reattempt the pair request in Xcode.

### URLSession

#### New Features

- The URLSession HTTP/2 implementation has been updated to support HTTP/2 connection reuse per RFC 7540 Section 9.1.1. This requires an HTTP/2 server to present a certificate which covers more than one server hostname. The certificate may use the Subject Alternative Name extension or wildcarded domain names. In addition, URLSession requires name resolution to resolve the different hostnames to the same IP address. URLSession might reuse HTTP/2 connections across different domain names when these conditions are satisfied. (37507838)

#### Deprecations

- The `ftp://` and `file://` URL schemes for Proxy Automatic Configuration (PAC) are deprecated. HTTP and HTTPS are the only supported URL schemes for PAC. This affects all PAC configurations including, but not limited to, configurations set via Settings, System Preferences, profiles, and URLSession APIs such as connectionProxyDictionary, and CFNetworkExecuteProxyAutoConfigurationURL(_:_:_:_:). (37811761)

### On-Demand Resources

#### Known Issues

- The new build system in Xcode doesn’t support On Demand Resources (ODR). (31508570)

  **Workaround:** Use the legacy build system for projects requiring ODR (File \> Project/Workspace Settings).

## See Also

### tvOS 12

tvOS 12.4 Release Notes

Update your apps to use new features, and test your apps against API changes.

tvOS 12.2 Release Notes

Update your apps to use new features, and test your apps against API changes.

tvOS 12.1.2 Release Notes

Update your apps to use new features, and test your apps against API changes.

tvOS 12.1.1 Release Notes

Update your apps to use new features, and test your apps against API changes.

