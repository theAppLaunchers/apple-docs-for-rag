

- Device Management
-  CertificatePKCS12 

Device Management Profile

# CertificatePKCS12

The payload you use to configure a PKCS \#12-formatted certificate.

iOS 4.0+iPadOS 4.0+macOS 10.7+tvOS 9.0+visionOS 1.0+watchOS 3.0+Device Assignment ServicesVPP License Management

``` source
object CertificatePKCS12
```

## Properties

`AllowAllAppsAccess`

`boolean`

If `true`, the system allows apps access to the private key. Available in macOS 10.10 and later.

Default: `false`

`KeyIsExtractable`

`boolean`

If `false`, the system doesn’t tag the private key data as extractable in the keychain.

Default: `true`

`Password`

`string`

The password to the identity.

`PayloadCertificateFileName`

`string`

The file name of the enclosed certificate.

`PayloadContent`

`data`

 (Required) 

The binary representation of the payload, encoded in Base64.

## Discussion

Specify `com.apple.security.pkcs12` as the payload type.

Warning

The system obfuscates the profile but doesn’t encrypt it, so it’s possible to intercept the profile and extract the password and identity.

It’s recommended to omit the password in the profile, or do one of the following instead:

- Securely deliver the profile to authorized users only, such as through MDM.

- Encrypt the profile so that only authorized devices can decrypt it.

- Use SCEP or ACMECertificate to provision the identity.

### Profile Availability

|                            |                                        |
|----------------------------|----------------------------------------|
| Device Channel             | iOS, macOS, Shared iPad, tvOS, watchOS |
| User Channel               | macOS                                  |
| Allow Manual Install       | iOS, macOS, Shared iPad, tvOS, watchOS |
| Requires Supervision       | \-                                     |
| Requires User Approved MDM | \-                                     |
| Allowed in User Enrollment | iOS, macOS                             |
| Allow Multiple Payloads    | iOS, macOS, Shared iPad, tvOS, watchOS |

### Example Profile

```

    PayloadContent

            Password
            Password123
            PayloadContent

            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
            BEdyH55ZZP2AuQQIXL1je1c7MRgCAQE=

            PayloadDisplayName
            CertificatePKCS12
            PayloadIdentifier
            com.example.mycertpkcs12payload
            PayloadType
            com.apple.security.pkcs12
            PayloadUUID
            25cdd076-f1e7-4932-aa30-1d4240534fb0
            PayloadVersion
            1

    PayloadDisplayName
    CertificatePKCS12
    PayloadIdentifier
    com.example.myprofile
    PayloadType
    com.apple.security.pkcs12
    PayloadUUID
    918ee83d-ebd5-4192-bcd4-8b4feb750e4b
    PayloadVersion
    1

```

## See Also

### Certificates

object ACMECertificate

The payload you use to configure Automated Certificate Management Environment (ACME) Certificate settings.

object ActiveDirectoryCertificate

The payload you use to configure Active Directory Certificate settings.

object CertificatePEM

The payload you use to configure a PEM-formatted certificate.

object CertificatePKCS1

The payload you use to configure a PKCS \#1-formatted certificate.

object CertificateRoot

The payload you use to configure a root certificate.

object CertificatePreference

The payload you use to configure a certificate preference.

object CertificateRevocation

The payload you use to configure certificate revocation checking.

object CertificateTransparency

The payload you use to configure certificate transparency enforcement.

object SCEP

The payload you use to configure Simple Certificate Enrollment Protocol (SCEP).

