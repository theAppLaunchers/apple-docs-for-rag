

- Security
-  kSecKeyLabel 

Global Variable

# kSecKeyLabel

macOS 10.0+

``` source
var kSecKeyLabel: Int32 { get }
```

## Discussion

Type blob; for private and public keys this contains the hash of the public key. This is used to associate certificates and keys. Its value matches the value of the `kSecPublicKeyHashItemAttr` attribute of a certificate and it’s used to construct an identity from a certificate and a key. For symmetric keys this is whatever the creator of the key passed in when they generated the key.

