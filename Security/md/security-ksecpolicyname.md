

- Security
-  kSecPolicyName 

Global Variable

# kSecPolicyName

A name (`CFStringRef`) that the certificate must match to satisfy this policy. For SSL/TLS, this specifies the server name which must match the common name of the certificate. For S/MIME, this specifies the RFC 822 email address.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+macOS 10.7+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
let kSecPolicyName: CFString
```

