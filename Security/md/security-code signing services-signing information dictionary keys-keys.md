

- Security
- Code Signing Services
-  Signing Information Dictionary Keys 

API Collection

# Signing Information Dictionary Keys

Use these keys from the information dictionary when you retrieve information from a code signature.

## Overview

Use these keys when examining the dictionary returned by the SecCodeCopySigningInformation(_:_:_:) function to obtain information about the signed code.

## Topics

### Constants

let kSecCodeInfoCdHashes: CFString

A key whose value is an array containing the unique binary identifier for every digest algorithm supported in the signature.

let kSecCodeInfoCertificates: CFString

A key whose value is an array of certificates representing the certificate chain of the signing certificate as seen by the system.

let kSecCodeInfoChangedFiles: CFString

A key whose value is a list of all files in the code that may have been modified by the process of signing it.

let kSecCodeInfoCMS: CFString

A key whose value is the CMS cryptographic object that secures the code signature.

let kSecCodeInfoDesignatedRequirement: CFString

A keys whose value is the designated requirement of the code.

let kSecCodeInfoDigestAlgorithm: CFString

A key whose value is a number indicating the cryptographic hash function.

let kSecCodeInfoDigestAlgorithms: CFString

A key whose value is a list of the kinds of cryptographic hash functions available within the signature.

let kSecCodeInfoEntitlements: CFString

A key whose value represents the embedded entitlement blob of the code, if any.

let kSecCodeInfoEntitlementsDict: CFString

A key whose value is a dictionary of embedded entitlements.

let kSecCodeInfoFormat: CFString

A key whose value is a string representing the type and format of the code in a form suitable for display to a knowledgeable user.

let kSecCodeInfoFlags: CFString

A key whose value indicates the static (on-disk) state of the object.

let kSecCodeInfoIdentifier: CFString

A key whose value is the signing identifier sealed into the signature.

let kSecCodeInfoImplicitDesignatedRequirement: CFString

A key whose value is the designated requirement (DR) that the system generated—or would have generated—for the code in the absence of an explicitly-declared DR.

let kSecCodeInfoMainExecutable: CFString

A key whose value is a URL locating the main executable file of the code.

let kSecCodeInfoPList: CFString

A key whose value is an information dictionary containing the contents of the secured `Info.plist` file as seen by Code Signing Services.

let kSecCodeInfoPlatformIdentifier: CFString

A key whose value identifies the operating system release with which the code is associated, if any.

let kSecCodeInfoRequirements: CFString

A key whose value is the internal requirements of the code as a text string in canonical syntax.

let kSecCodeInfoRequirementData: CFString

A key whose value is the internal requirements of the code as a binary blob.

let kSecCodeInfoRuntimeVersion: CFString

A key whose value represents the runtime version.

let kSecCodeInfoSource: CFString

The source of the code signature used for the code object in a format suitable for display.

let kSecCodeInfoStatus: CFString

A key whose value is the set of code status flags for the running code.

let kSecCodeInfoTeamIdentifier: CFString

A key whose value is the team identifier.

let kSecCodeInfoTime: CFString

A key whose value is the signing date embedded in the code signature.

let kSecCodeInfoTimestamp: CFString

A key whose value indicates the actual signing date.

let kSecCodeInfoTrust: CFString

A key whose value is the trust object the system uses to evaluate the validity of the code’s signature.

let kSecCodeInfoUnique: CFString

A key whose value is a binary number that uniquely identifies static code.

