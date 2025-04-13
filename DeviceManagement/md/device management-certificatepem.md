

- Device Management
-  CertificatePEM 

Device Management Profile

# CertificatePEM

The payload you use to configure a PEM-formatted certificate.

iOS 4.0+iPadOS 4.0+macOS 10.7+tvOS 9.0+visionOS 1.0+watchOS 3.0+Device Assignment ServicesVPP License Management

``` source
object CertificatePEM
```

## Properties

`PayloadCertificateFileName`

`string`

The file name of the enclosed certificate.

`PayloadContent`

`data`

 (Required) 

The binary representation of the payload, encoded in Base64.

## Discussion

Specify `com.apple.security.pem` as the payload type.

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

            PayloadContent

            LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSURTakNDQWpL
            Z0F3SUJBZ0lCQVRBTkJna3Foa2lHOXcwQkFRc0ZBREJLTVJZd0ZB
            WURWUVFEREExdFkzaDIKWVd4cFpHRjBhVzl1TVFzd0NRWURWUVFH
            RXdKVlV6RWpNQ0VHQ1NxR1NJYjNEUUVKQVJZVWNtOWljMjl1WDJG
            agpRR2xqYkc5MVpDNWpiMjB3SGhjTk1UZ3dNakUwTVRrMU9UUXpX
            aGNOTWpBd01qRTBNVGsxT1RReldqQktNUll3CkZBWURWUVFEREEx
            dFkzaDJZV3hwWkdGMGFXOXVNUXN3Q1FZRFZRUUdFd0pWVXpFak1D
            RUdDU3FHU0liM0RRRUoKQVJZVWNtOWljMjl1WDJGalFHbGpiRzkx
            WkM1amIyMHdnZ0VpTUEwR0NTcUdTSWIzRFFFQkFRVUFBNElCRHdB
            dwpnZ0VLQW9JQkFRQ3luNzR2Szh2NXRHU2NqK1pieHZhWWl5ZFFD
            cUtUNjFEVzlEdlM1bW4xcCtJcEp6M3hJdFI1Cnd6NCtXTmFzbWRt
            ek11L3BuRUkwaXA0SUxYaHpFUVpieHlIZElGQU1LTWNHTzZuekla
            S3NiZ2MveE1WcVJyM0YKWExTOTY4Vlg3djd2SFVxRFpveDhhMHVn
            b1NlM2ZIeEl1Z2FMTldRL0RYeE1mbllJQ0k4azNndXFtQ3Zib3No
            UwpaTnFhYXNLUlNzWWZFYlRZTUNkSVBYMnBDNDNGMzYyNE16R2RV
            RDZSYjJWZDRUamNQZXVINjVkdDhrbXI3NTc0Cjc5MDF2Zlp3ZDds
            UzFITHozcHdQa0s1UlZnOVU0dHJ5Y0xKUmJWSm9mTUhRUWJIMEZ4
            TWUxTUhpRmx4c1pwYjMKQTl1SDRjYzVyWlRocmpIeUlkTTZPZVoy
            UWVWQ1ZMR3ZBZ01CQUFHak96QTVNQThHQTFVZEV3RUIvd1FGTUFN
            QgpBUUF3RGdZRFZSMFBBCCgvQkFRREFnZUFNQllHQTFVZEpRRUIv
            d1FNTUFvR0NDc0dBUVVGQndNQ01BMEdDU3FHClNJYjNEUUVCQ3dV
            QUE0SUJBUUJ6RTdvdnRBRnVEWDNXQVFuMjc0K2NLTUsvT3JEK050
            dGJxZ2x0ZUFLV250ZlAKTk45VXFmSzhZaTBtZDEvQ3V4OEhWYXp5
            N0ZmdjlXZExHZjFJeDJoczAzcFVJalZUWmZHeWlac2Rhazd6NXZl
            YgpmdXFZT3F5L0VDUElxR2ZSYkxFeW9SZ0RUeTM2ODIzWUJ4bVdm
            bWV1SlFmQVdhTHFvbUd1Z0R6RDVPTFWKWHdHCml2MVdFc0dXYWhT
            Vzlxb3llSkhFcE5tamZ1c1BmSTd4UnY3Q1ByeXh1U2hEakFYdXl5
            cmdqVm5HdjUrdENzNnIKODNQd1NjdUhydU41Ymc4THE5bW9pVnpa
            Qy9WdGRFbTN6TzVwUnFjd0NRanZmUjUvVWJsT2Z5N2x5WkNlWUU3
            SApXKzlLUzdCbmVtRnBBSFhvU296b1M3WW1YQnhmT1BqbDB6MEhW
            V2VsCi0tLS0tRU5EIENFUlRJRklDQVRFLS0tLS0K

            PayloadIdentifier
            com.example.mycertpempayload
            PayloadType
            com.apple.security.pem
            PayloadUUID
            b740fbbc-ad70-4f59-b6f5-40887d284a70
            PayloadVersion
            1

    PayloadDisplayName
    CertificatePEM
    PayloadIdentifier
    com.example.profile
    PayloadType
    Configuration
    PayloadUUID
    0d198a1e-7d38-48f5-ad67-422382c1c9e7
    PayloadVersion
    1

```

## See Also

### Certificates

object ACMECertificate

The payload you use to configure Automated Certificate Management Environment (ACME) Certificate settings.

object ActiveDirectoryCertificate

The payload you use to configure Active Directory Certificate settings.

object CertificatePKCS1

The payload you use to configure a PKCS \#1-formatted certificate.

object CertificatePKCS12

The payload you use to configure a PKCS \#12-formatted certificate.

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

