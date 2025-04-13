

- Security
- Certificate, Key, and Trust Services
- Certificates
-  Examining a Certificate 

Article

# Examining a Certificate

Learn how to retrieve properties from a certificate.

## Overview

In order to fulfill its purpose of verifying the identity of its owner, a certificate contains such information as:

- The certificate issuer

- The certificate holder

- A validity period (the certificate isn’t valid before or after this period)

- The public key of the certificate’s owner

- *Certificate extensions*, which contain additional information such as alternative names for the certificate holder and allowable uses for the private key associated with the certificate

- A digital signature from the certification authority to ensure that the certificate hasn’t been altered and to indicate the identity of the issuer

The certificate, key, and trust services API provides functions to examine the properties of a certificate. For example, the SecCertificateCopySubjectSummary(_:) function returns a human readable summary of the certificate:

- Swift
- Objective-C

```
let certificate = 
let summary = SecCertificateCopySubjectSummary(certificate) as String
print("Cert summary: \(summary)")
```

```
SecCertificateRef certificate = ;
NSString* summary = (NSString*)CFBridgingRelease(  // ARC takes ownership
                       SecCertificateCopySubjectSummary(certificate)
                    );
NSLog(@"Cert summary: %@", summary);
```

In macOS, there are a few additional functions that return data about a certificate. For example, to pull the public key from a certificate, you use the SecCertificateCopyPublicKey(_:) function:

- Swift
- Objective-C

```
var publicKey: SecKey?
let status = SecCertificateCopyPublicKey(certificate, &publicKey)
guard status == errSecSuccess else { throw  }
```

```
SecKeyRef publicKey = NULL;
OSStatus status = SecCertificateCopyPublicKey(certificate, &publicKey);
if (status != errSecSuccess) {  }
else                         {  }

if (publicKey) { CFRelease(publicKey); }  // After you are done with it
```

