

- App License Delivery SDK
-  Configuring your app licensing environment 

Article

# Configuring your app licensing environment

Create your account-level signing assets and build the SDK for your target platform.

## Overview

After your developer account qualifies to build an alternative app marketplace, you can use App License Delivery SDK to secure the installation of your marketplace app and the apps that you distribute from your alternative marketplace. To set up your development environment for app licensing:

- Create your App License Delivery signing assets.

- Build the SDK on your target platform (macOS or Linux).

For more information about alternative app marketplaces, see MarketplaceKit.

## Generate alternative marketplace app licensing assets

To facilitate generating licenses, create the following App License Delivery (ALD) assets in Certificates, Identifiers &amp; Profiles:

Encryption certificate  
Decrypts license requests that a device sends to your licensing endpoint.

Signing certificate  
Signs licenses you create and verifies their authenticity on device.

PASK  
A secret that secures the transport of app key blobs.

For more information about generating these assets, see Create app license delivery certificates.

Important

Secure your PASK secret as you do other credentials, such as private keys and passwords. Don’t share your PASK secret, store secrets in a code repository, or include secrets in client or server code.

## Build the SDK for macOS

To use the SDK in a Swift project for macOS:

1.  Expand the SDK archive.

2.  In Xcode, choose the File menu \> Add Package Dependencies…

3.  In the package dependencies window, click Add Local…

4.  In the file bowser, choose the expanded SDK archive folder.

5.  Import `ALD` in your Swift licensing source files:

```
```

## Build the SDK for Linux

To build the SDK for Linux:

1.  Download a Swift container from https://www.swift.org/download.

2.  Choose Ubuntu 22.04 for `x86_64` with Swift Docker tag `5.9-jammy`.

3.  Install the Docker container and start it.

4.  Copy the `aldsdk` archive file (with the `.tar` file extension) into the container and expand it.

5.  In Terminal, navigate to the `aldsdk` root directory.

6.  Run the following command to build the SDK and produce an example license:

```
swift test -c release --triple x86_64-unknown-linux-gnu \
    -Xbuild-tools-swiftc -Dx86_64_linux_gnu_TRIPLE
```

Tip

If you’re using Docker Desktop, disable Rosetta after you install the Docker container.

