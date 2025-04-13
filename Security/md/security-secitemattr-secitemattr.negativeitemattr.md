

- Security
- SecItemAttr
-  SecItemAttr.negativeItemAttr 

Case

# SecItemAttr.negativeItemAttr

Identifies the negative attribute.

Mac Catalyst 13.0+macOS 10.0+

``` source
case negativeItemAttr
```

## Discussion

You use this tag to set or get a value of type `Boolean` that indicates whether there is a valid password associated with this keychain item. This is useful if your application doesn’t want a password for some particular service to be stored in the keychain, but prefers that it always be entered by the user. The item, which is typically invisible and with zero-length data, acts as a placeholder.

