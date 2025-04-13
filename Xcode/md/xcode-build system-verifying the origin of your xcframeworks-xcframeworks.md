

- Xcode
- Build system
-  Verifying the origin of your XCFrameworks 

Article

# Verifying the origin of your XCFrameworks

Discover who signed a framework, and take action when that changes.

## Overview

When you add third-party binary SDKs to your target as XCFrameworks, the behaviors of those packages become part of the behavior of your product. An attacker who’s able to inject a compromised version of the SDK into your project could change your app’s behavior and cause security and privacy issues for your developers, testers, and people who use your product.

Use Xcode to inspect the information in the code signature embedded in an XCFramework when you add it to your project. The build system fails with an error if the code signature’s subsequently removed, becomes invalid, or a different developer signs an update to the framework. If any of these happens, take action to resolve the issue.

### Inspect a dependency’s code signing identity

In Xcode, select your dependency’s XCFramework folder in the Project navigator. The File inspector shows you the XCFramework’s code signing status. If the framework is signed with an Apple Developer certificate, the inspector also shows which team signed the framework.

If the XCFramework is signed by a self-issued code signing identity, the inspector shows the SHA-256 fingerprint of the certificate in the framework’s code signature. Verify that the certificate fingerprint matches the value you expect.

### Diagnose build failures caused by code signature changes

An XCFramework’s code signature can change for legitimate reasons, like:

- the provider of a third-party SDK transfers ownership of the SDK to another organization, who release a version that’s signed with the new organization’s Team ID.

- you switch from a vendor-supplied distribution of an XCFramework to a version that you build and sign yourself.

A changed code signature can also indicate that the XCFramework has been tampered with, or another actor has injected their own code into your system, pretending it’s a version of the XCFramework.

If the code signature for an XCFramework changes, Xcode shows the changed code signature information in the File inspector.

If you attempt to build the software without resolving the changed code signature information, the build system produces an error. Work with the XCFramework’s provider to determine whether the change is expected. If the change is expected, follow these steps:

1.  Switch to the Issues navigator.

2.  Select the error that says “\[XCFramework name\] is not signed with the expected identity and may have been compromised”.

3.  In the dialog that appears, click Accept Change.

If your team and the SDK provider can’t account for the change to the XCFramework’s code signature, restore a version of the framework with the expected code signature, or remove the framework from your project. To restore the framework to a version with the expected code signature, do the following:

1.  In the dialog, click Move to Trash.

2.  Switch to or open a new Finder window.

3.  Drag a replacement copy of the XCFramework from a trusted source to the Finder folder that contained the copy you deleted.

4.  Switch to Xcode, and verify that the XCFramework’s signature is valid in the File inspector.

Warning

If you encounter an unexpected code signature change in an XCFramework, it’s possible that an attacker is exploiting a security vulnerability in your infrastructure. Audit the origins for your XCFrameworks to ensure you obtained them from official sources. You also need to audit your software development and deployment environment carefully, even if you revert the XCFramework to a correctly-signed version.

Xcode also warns you if the XCFramework is signed with an expired or revoked code signing identity, even if the identity hasn’t changed since you added the XCFramework to your project. If this happens, work with the SDK provider to obtain a new version of the framework that’s signed by a valid code signing identity.

### Diagnose failures caused when a code signature is removed

If someone removes the code signature for an XCFramework, Xcode shows the change in the File inspector.

The build system fails with an error if you attempt to build the software without resolving the removed code signature. Determine why the code signature is missing from the XCFramework. If you no longer expect the XCFramework to be signed, follow these steps:

1.  Switch to the Issues navigator.

2.  Select the error that says “\[XCFramework name\] is not signed with the expected identity and may have been compromised”.

3.  In the dialog that appears, click Accept Change.

