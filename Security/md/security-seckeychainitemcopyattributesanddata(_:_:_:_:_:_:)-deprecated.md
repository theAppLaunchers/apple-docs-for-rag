

- Security
-  SecKeychainItemCopyAttributesAndData(\_:\_:\_:\_:\_:\_:) Deprecated

Function

# SecKeychainItemCopyAttributesAndData(\_:\_:\_:\_:\_:\_:)

Retrieves the data and/or attributes stored in the given keychain item.

macOS 10.2–10.10Deprecated

``` source
func SecKeychainItemCopyAttributesAndData(
    _ itemRef: SecKeychainItem,
    _ info: UnsafeMutablePointer?,
    _ itemClass: UnsafeMutablePointer?,
    _ attrList: UnsafeMutablePointer?>?,
    _ length: UnsafeMutablePointer?,
    _ outData: UnsafeMutablePointer?
) -> OSStatus
```

Deprecated

SecKeychain is deprecated

## Parameters 

`itemRef`  

A reference to the keychain item from which you wish to retrieve data or attributes.

`info`  

A pointer to a list of tags and formats of attributes to retrieve. You can call SecKeychainAttributeInfoForItemID(_:_:_:) to obtain a list of all possible attribute tags and formats for the item’s class. Pass `NULL` if you don’t wish to retrieve any attributes.

`itemClass`  

On return, the item’s class. Pass `NULL` if not required. See SecItemClass for valid constants.

`attrList`  

On return, the retrieved attributes and their values . Pass `NULL` if not required. You must call the function SecKeychainItemFreeAttributesAndData(_:_:) when you no longer need the attributes and values.

`length`  

On return, the actual length of the data returned in the `outData` parameter.

`outData`  

On return, the data in this item. Pass `NULL` if not required. You must call the function SecKeychainItemFreeAttributesAndData(_:_:) when you no longer need the data.

## Return Value

A result code. See Security Framework Result Codes.

## Discussion

This function returns the data and attributes of a specific keychain item.

Note

This is a CSSM-based API. CSSM is deprecated.

For new development, where possible, you should generally use SecItemCopyMatching(_:_:) to obtain attributes of keychain items instead, because that function is based on Core Foundation types.

You can use the SecKeychainSearchCopyNext function to search for a keychain item if you don’t already have the item’s reference object. To find and obtain data from a password keychain item, use the SecKeychainFindInternetPassword(_:_:_:_:_:_:_:_:_:_:_:_:_:_:_:) or SecKeychainFindGenericPassword(_:_:_:_:_:_:_:_:) function.

You should pair the `SecKeychainItemCopyAttributesAndData` function with the SecKeychainItemModifyAttributesAndData(_:_:_:_:) function, as these functions handle more attributes than are support by the old Keychain Manager and passing them into older calls yields an invalid attribute error. Use the functions SecKeychainItemModifyContent(_:_:_:_:) and SecKeychainItemCopyContent(_:_:_:_:_:) when dealing with older Keychain Manager functions.

If the keychain item data is encrypted, this function decrypts the data before returning it to you. If the calling application is not in the list of trusted applications, the user is prompted before access is allowed. If the access controls for this item do not allow decryption, the function returns the `errSecAuthFailed` result code.

