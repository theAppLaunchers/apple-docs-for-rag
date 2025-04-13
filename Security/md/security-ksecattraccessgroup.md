

- Security
-  kSecAttrAccessGroup 

Global Variable

# kSecAttrAccessGroup

A key with a value that’s a string indicating the access group the item is in.

iOS 3.0+iPadOS 3.0+Mac Catalyst 13.1+macOS 10.9+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
let kSecAttrAccessGroup: CFString
```

## Mentioned in 

Sharing access to keychain items among a collection of apps

Searching for keychain items

## Discussion

The corresponding value is of type CFString and indicates the item’s one and only access group.

For an app to access a keychain item, one of the groups to which the app belongs must be the item’s group. The list of an app’s access groups consists of the following string identifiers, in this order:

- The strings in the app’s Keychain Access Groups Entitlement

- The app ID string

- The strings in the App Groups Entitlement

Two or more apps that are in the same access group can share keychain items. For more details, see Sharing access to keychain items among a collection of apps.

Specify which access group a keychain item belongs to when you create it by setting the kSecAttrAccessGroup attribute in the query you send to the SecItemAdd(_:_:) method. Naming a group that’s not among the creating app’s access groups—including the empty string, which is always an invalid group—generates an error. If you don’t explicitly set a group, keychain services defaults to the app’s first access group, which is either the first keychain access group, or the app ID when the app has no keychain groups. In the latter case, the item is only accessible to the app creating the item, since no other app can be in that group.

By default, the SecItemUpdate(_:_:), SecItemDelete(_:), and SecItemCopyMatching(_:_:) methods search all the app’s access groups. Add the kSecAttrAccessGroup attribute to the query to limit the search to a particular group.

Important

This attribute applies to macOS keychain items only if you also set a value of `true` for the kSecUseDataProtectionKeychain key, the kSecAttrSynchronizable key, or both.

## See Also

### Related Documentation

Sharing access to keychain items among a collection of apps

Enable apps to share keychain items with each other by adding the apps to an access group.

