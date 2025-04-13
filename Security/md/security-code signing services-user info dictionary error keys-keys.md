

- Security
- Code Signing Services
-  User Info Dictionary Error Keys 

API Collection

# User Info Dictionary Error Keys

Recognize the keys of the user info dictionary provided by functions that return error objects.

## Overview

Code Signing Services functions that return an error on failure may provide additional information by populating the error’s user info dictionary with any of these keys. Use the CFErrorCopyUserInfo(_:) function to retrieve the user info dictionary from the error object.

These keys are always supplemental and optional. Don’t rely on their presence or absence to categorize an error. Use the primary `OSStatus` return codes listed in Code Signing Services Result Codes for that.

## Topics

### Constants

let kSecCFErrorArchitecture: CFString

A key whose value is a string containing the name of the architecture that is causing the problem.

let kSecCFErrorPattern: CFString

A key whose value is a string containing a regular expression that’s part of a resource specification that did not parse correctly.

let kSecCFErrorResourceSeal: CFString

A key whose value is a Core Foundation object containing the part of the resource seal that had a problem.

let kSecCFErrorResourceAdded: CFString

A key whose value is a URL pointing to the resource on disk that is not included in the signed resources for the code.

let kSecCFErrorResourceAltered: CFString

A key whose value is a URL pointing to the resource on disk that has been altered.

let kSecCFErrorResourceMissing: CFString

A key whose value is a URL indicating the location of the missing resource as it is specified in the `CodeResources` file.

let kSecCFErrorResourceSideband: CFString

A key whose value is a URL representing a sealed resource with invalid sideband data (resource fork, etc.).

let kSecCFErrorInfoPlist: CFString

A key whose value is a Core Foundation object identifying the invalid component or key in the dictionary.

let kSecCFErrorGuestAttributes: CFString

A key whose value is a Core Foundation object containing an attribute that is unrecognized or that contains a value of the wrong type.

let kSecCFErrorRequirementSyntax: CFString

A key whose value is a string containing a compilation error generated when parsing a requirement.

let kSecCFErrorPath: CFString

A key whose value is a URL indicating the subcomponent containing the error.

