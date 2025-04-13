

- Security
- Certificate, Key, and Trust Services
- Keys
-  Storing Keys as Data 

Article

# Storing Keys as Data

Create an external representation of a key for transmission.

## Overview

If you have a key that you want to send somewhere, you package it in a form that’s suitable for transmission.

### Export the Key as a Data Instance

Create a data instance representing a key using the SecKeyCopyExternalRepresentation(_:_:) function:

- Swift
- Objective-C

```
let key = 
var error: Unmanaged?
guard let data = SecKeyCopyExternalRepresentation(key, &error) as Data else {
    throw error!.takeRetainedValue() as Error
}
```

```
SecKeyRef key = ;
CFErrorRef error = NULL;
NSData* keyData = (NSData*)CFBridgingRelease(  // ARC takes ownership
                       SecKeyCopyExternalRepresentation(key, &error)
                   );
if (!keyData) {
    NSError *err = CFBridgingRelease(error);  // ARC takes ownership
    // Handle the error. . .
}

```

The data instance returned from this function can then be sent across a network, through the file system, or by any other means, so long as the data’s content is preserved exactly.

This method works for both public and private keys. However, it doesn’t work for all keys. For example, if a key is bound to a smart card or to the Secure Enclave, you can’t export it this way. Also, in macOS, a key that has the kSecKeyExtractable attribute set to false is ineligible for export. In these cases, or if any other error occurs, the returned data is `nil` and the error object indicates the reason for failure.

When an error does occur, you become responsible for the error object’s memory. In Objective-C, you transfer ownership to Automatic Reference Counting (ARC) using a call to CFBridgingRelease. In Swift, you convert the unmanaged doc://com.apple.documentation/documentation/corefoundation/cferror-ru8 object to a managed Error using takeRetainedValue() and a cast.

The format of the returned data depends on the kind of key you are exporting:

- For an RSA key, the function returns data in the PKCS \#1 format.

- For an elliptic curve public key, the format follows the ANSI X9.63 standard using a byte string of `04 || X || Y`.

- For an elliptic curve private key, the output is formatted as the public key concatenated with the big endian encoding of the secret scalar, or `04 || X || Y || K`.

All of these representations use constant size integers, including leading zeros as needed.

Avoid insecure distribution of cryptographic keys, and pay special attention to private keys. You can distribute a public key freely, although you do need to ensure trust—can the receiver be sure this is the public key that you sent? Trust is typically established with a signed certificate, but if you are working in a closed system, or enforce trust in some other way, you can export and send public keys as data. Use extra caution, however, when exporting private keys, because they must remain absolutely secret to be of value.

Important

If there’s even a possibility that an untrusted entity has gained access to your private key, it is compromised and you should stop using it.

### Restore a Key from a Data Instance

When you’re ready to restore the data instance back into a key, use the SecKeyCreateWithData(_:_:_:) function:

- Swift
- Objective-C

```
let options: [String: Any] = [kSecAttrKeyType as String: kSecAttrKeyTypeRSA,
                              kSecAttrKeyClass as String: kSecAttrKeyClassPublic]
var error: Unmanaged?
guard let key = SecKeyCreateWithData(data as CFData,
                                     options as CFDictionary,
                                     &error) else {
                                        throw error!.takeRetainedValue() as Error
}
```

```
// The key is assumed to be public, 2048-bit RSA
NSDictionary* options = @{(id)kSecAttrKeyType: (id)kSecAttrKeyTypeRSA,
                          (id)kSecAttrKeyClass: (id)kSecAttrKeyClassPublic
                         };
CFErrorRef error = NULL;
SecKeyRef key = SecKeyCreateWithData((__bridge CFDataRef)data,
                                     (__bridge CFDictionaryRef)options,
                                     &error);
if (!key) {
    NSError *err = CFBridgingRelease(error);  // ARC takes ownership
    // Handle the error. . .
} else {  }

if (key) { CFRelease(key); }  // After you are done with it
```

In this case, you use an options dictionary to inform the function about certain characteristics of the key. At a minimum, you indicate the key’s type and class, which means you need to communicate this information along with the key data or establish it ahead of time. If the function returns an empty key reference, check the error object for indications of failure.

In Objective-C, you release the key object’s memory after you’re done using it. You also transfer ownership of the error object, if it exists, to ARC. In Swift, the key object’s memory is already managed by the system, but you transfer ownership of the unmanaged doc://com.apple.documentation/documentation/corefoundation/cferror-ru8 to the system with takeRetainedValue() and recast it as an Error before throwing it.

