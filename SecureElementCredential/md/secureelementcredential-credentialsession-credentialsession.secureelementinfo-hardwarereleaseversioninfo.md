

- SecureElementCredential
- CredentialSession
- CredentialSession.SecureElementInfo
-  hardwareReleaseVersionInfo 

Instance Property

# hardwareReleaseVersionInfo

A string that encodes the hardware and software release versions of the Secure Element.

iOS 18.4+iPadOS 18.4+

``` source
let hardwareReleaseVersionInfo: String
```

## Discussion

Use this string to determine eligibility or select which applet bundle, previously submitted to Apple Business Register (ABR), to install on this device.

This string uses the format `"JCOP X.Y"`, with the following semantics:

X  
An integer that corresponds to the chip type.

Y  
An integer that corresponds to the release iteration.

For more details, see the Mobile Secure Element specification from ABR.

## See Also

### Getting hardware information

let secureElementPlatformSigningCertificate: Data

A certificate you use to authenticate against the Certification Authority of the Secure Element hardware.

