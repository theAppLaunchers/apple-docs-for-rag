

- Security
-  kSecAttrAccessibleAfterFirstUnlockThisDeviceOnly 

Global Variable

# kSecAttrAccessibleAfterFirstUnlockThisDeviceOnly

The data in the keychain item cannot be accessed after a restart until the device has been unlocked once by the user.

iOS 4.0+iPadOS 4.0+Mac Catalyst 13.1+macOS 10.9+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
let kSecAttrAccessibleAfterFirstUnlockThisDeviceOnly: CFString
```

## Discussion

After the first unlock, the data remains accessible until the next restart. This is recommended for items that need to be accessed by background applications. Items with this attribute *do not* migrate to a new device. Thus, after restoring from a backup of a different device, these items will not be present.

