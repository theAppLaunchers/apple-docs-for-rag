

- Device Management
-  CertificateRoot 

Device Management Profile

# CertificateRoot

The payload you use to configure a root certificate.

iOS 4.0+iPadOS 4.0+macOS 10.7+tvOS 9.0+visionOS 1.0+watchOS 3.0+Device Assignment ServicesVPP License Management

``` source
object CertificateRoot
```

## Properties

`PayloadCertificateFileName`

`string`

The file name of the enclosed certificate.

`PayloadContent`

`data`

 (Required) 

The binary representation of the payload encoded in base64.

## Discussion

Specify `com.apple.security.root` as the payload type.

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

### Profile Example

```

    PayloadContent

            PayloadCertificateFileName
            CertificateRoot
            PayloadContent

            MIIFkjCCBHqgAwIBAgIGAVGFkFcjMA0GCSqGSIb3DQEBCwUAMIHN
            MV8wXQYDVQQDDFZDaGFybGVzIFByb3h5IEN1c3RvbSBSb290IENl
            cnRpZmljYXRlIChidWlsdCBvbiBHcmFoYW1zLU1hY0Jvb2stUHJv
            LmxvY2FsLCA4IERlYyAyMDE1KTEkMCIGA1UECwwbaHR0cDovL2No
            YXJsZXNwcm94eS5jb20vc3NsMREwDwYDVQQKDAhYSzcyIEx0ZDER
            MA8GA1UEBwwIQXVja2xhbmQxETAPBgNVBAgMCEF1Y2tsYW5kMQsw
            CQYDVQQGEwJOWjAeFw0wMDAxMDEwMDAwMDBaFw00NTAyMDQwNzA2
            NDdaMIHNMV8wXQYDVQQDDFZDaGFybGVzIFByb3h5IEN1c3RvbSBS
            b290IENlcnRpZmljYXRlIChidWlsdCBvbiBHcmFoYW1zLU1hY0Jv
            b2stUHJvLmxvY2FsLCA4IERlYyAyMDE1KTEkMCIGA1UECwwbaHR0
            cDovL2NoYXJsZXNwcm94eS5jb20vc3NsMREwDwYDVQQKDAhYSzcy
            IEx0ZDERMA8GA1UEBwwIQXVja2xhbmQxETAPBgNVBAgMCEF1Y2ts
            YW5kMQswCQYDVQQGEwJOWjCCASIwDQYJKoZIhvcNAQEBBQADggEP
            ADCCAQoCggEBALZ+RVqfvyCzq6/q+kS3BdntLhaJi22GlOoHyx4L
            qgZl7T+wjjZ8gdM6lIm6P7WiKN86tVEqP/7rH6m5t/3IHMnE279H
            N6NSsiAkCw8WQiMkqxxJj4bBhuUcNP84d9b2zTqUqAbklQCuy/DA
            /rxJqcsbvqkbToJA5bWBX0wrGlpXlGr5do/K5t7bxpERh6T/m7W6
            S4Gc7ad3+l6izeue+8M5onCqXyu9Xcj+3wrXmzcndlNCv4mMvHEj
            Rpun/k5ECPBqju6jDou3YMCVOGMaRNZPagk2s/rFykY6mUfYG9Nl
            XRHP7zvtlxWyocsP7MoiXF3RtKZ+/A58T3cOs9/ZsvMCAwEAAaOC
            AXQwggFwMA8GA1UdEwEB/wQFMAMBAf8wggEsBglghkgBhvhCAQ0E
            ggEdE4IBGVRoaXMgUm9vdCBjZXJ0aWZpY2F0ZSB3YXMgZ2VuZXJh
            dGVkIGJ5IENoYXJsZXMgUHJveHkgZm9yIFNTTCBQcm94eWluZy4g
            SWYgdGhpcyBjZXJ0aWZpY2F0GSBpcyBwYXJ0IG9mIGEgY2VydGlm
            aWNhdGUgY2hhaW4sIHRoaXMgbWVhbnMgdGhhdCB5b3UncmUgYnJv
            d3NpbmcgdGhyb3VnaCBDaGFybGVzIFByb3h5IHdpdGggU1NMIFBy
            b3h5aW5nIGVuYWJsZWQgZm9yIHRoaXMgd2Vic2l0ZS4gUGxlYXNl
            IHNlZSBodHRwOi8vY2hhcmxlc3Byb3h5LmNvbS9zc2wgZm9yIG1v
            cmUgaW5mb3JtYXRpb24uMA4GA1UdDwEB/wQEAwICBDAdBgNVHQ4E
            FgQUcc8I4xXSdaFRISmIwGeCqhY6nhwwDQYJKoZIhvcNAQELBQAD
            ggEBADBuM0VZmxjQejORsGewl0Oy3K/Lfm5+STHiZH+cWACIQF4K
            EUMuf13/Hxy9EZbtckgDyOlT4lMge7PKYw/qrVo2Zm4xj1cVOHef
            +H4jRwoQ7UZBUAQhsQDMow408F6A6UY/AGdIGcrUp/ulQmMNr5+6
            yTnzm1RiMjajpTi9oxxV+1oUVSIMu7nk9qFplbCjEPxU8UB2R0YV
            d2vhaEdrdq1LwGTWj5sJiVBaFdzIu/ABV+H2Frij2wASrv1JdR2b
            uDTfgTacGqkfm6ajIlF5JyqXe1ZlIb38mlelg5maZNPjsljvNQ+F
            SnOctNmcbAmvH9FxsQ/wYThbkYM63Dii9EQ=

            PayloadDescription
            Adds Certificate Root
            PayloadDisplayName
            Example Root Certificate
            PayloadIdentifier
            com.example.mycertrootpayload
            PayloadType
            com.apple.security.root
            PayloadUUID
            6a20a2f5-97e5-4fd5-ac76-0d7708778e68
            PayloadVersion
            1

    PayloadDisplayName
    CertificateRoot
    PayloadIdentifier
    com.example.myprofile
    PayloadType
    Configuration
    PayloadUUID
    6594337c-742b-4841-bbed-76d79cdef34e
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

object CertificatePKCS12

The payload you use to configure a PKCS \#12-formatted certificate.

object CertificatePreference

The payload you use to configure a certificate preference.

object CertificateRevocation

The payload you use to configure certificate revocation checking.

object CertificateTransparency

The payload you use to configure certificate transparency enforcement.

object SCEP

The payload you use to configure Simple Certificate Enrollment Protocol (SCEP).

