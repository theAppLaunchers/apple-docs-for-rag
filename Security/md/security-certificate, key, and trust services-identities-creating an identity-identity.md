

- Security
- Certificate, Key, and Trust Services
- Identities
-  Creating an Identity 

Article

# Creating an Identity

Create an identity from a certificate and private key.

## Overview

In macOS, you can create an identity as a combination of a certificate and a private key. You begin by obtaining a certificate reference in one of the ways described in Getting a Certificate. You then supply that reference to the SecIdentityCreateWithCertificate(_:_:_:) function:

- Swift
- Objective-C

```
let certificate: SecCertificate = 
var identity: SecIdentity?
let status = SecIdentityCreateWithCertificate(nil, certificate, &identity)
guard status == errSecSuccess else { throw  }
```

```
SecCertificateRef certificate = ;
SecIdentityRef identity = NULL;
OSStatus status =
    SecIdentityCreateWithCertificate(NULL,   // Default keychain search list
                                     certificate,
                                     &identity);
if (status != errSecSuccess) {  }
else                         {  }

if (identity) { CFRelease(identity); }  // After you are done with it
```

The function attempts to locate the corresponding private key in the default keychain list or in the keychain or keychains that you specify as the first argument. If it succeeds, as indicated by the status result, it populates the identity reference with a pointer to a newly created identity object. Otherwise, the identity reference remains empty.

To persist a copy of the identity for later use, store it in the keychain, as described in Storing an Identity in the Keychain.

In Objective-C, when you are done with the identity, you are responsible for freeing the object’s memory. In Swift, the system manages the object’s memory automatically, releasing it when the object goes out of scope.

