

- Device Management
-  List the Certificates 

Web Service Endpoint

# List the Certificates

Get a list of installed certificates on a device.

iOS 4.0+iPadOS 4.0+macOS 10.7+tvOS 9.0+visionOS 1.1+watchOS 10.0+Device Assignment ServicesVPP License Management

## URL

``` source
PUT https://yourmdmhost.example.com/mdm#CertificateListCommand
```

## HTTP Body

CertificateListCommand

The command to get a list of installed certificates on a device.

Content-Type: application/x-apple-aspen-mdm

## Response Codes

` 200 ``OK`

CertificateListResponse

`OK`

A response from the device after it processes the command to get a list of installed certificates.

Content-Type: application/xml

## Discussion

This command allows the server to retrieve the list of installed certificates on the device. The command requires that the server has the Inspect Profile Manifest privilege. For user enrollment, this request returns only certificates pushed by MDM.

Starting with iOS 15.4, this command returns a Not Now response before the passcode-protected device’s first unlock after a device boots. Between iOS 15.0 and iOS 15.4, devices in that state didn’t respond with Not Now, but the response might not contain all identity certificates.

Refer to the following sections to determine supported channels and requirements, and to see an example request and response.

### Query Availability

|                            |                                        |
|----------------------------|----------------------------------------|
| Device Channel             | iOS, macOS, Shared iPad, tvOS, watchOS |
| User Channel               | macOS                                  |
| Requires Supervision       | \-                                     |
| Allowed in User Enrollment | iOS, macOS                             |
| Required Access Right      | AllowInspection                        |

### Example Request and Response

- Request
- Response

```

    Command

        ManagedOnly

        RequestType
        CertificateList

    CommandUUID
    0001_CertificateList

```

```

    CertificateList

            CommonName
            Example Root Cert
            Data

            MIIFeDCCA2ACCQC1lXUyZrOlDjANBgkqhkiG9w0BAQsFADB+MQsw
            CQYDVQQGEwJVUzETMBEGA1UECAwKQ2FsaWZvcm5pYTESMBAGA1UE
            BwwJQ3VwZXJ0aW5vMRMwEQYDVQQKDApBcHBsZSBJbmMuMRowGAYD
            VQQLDBFEZXZpY2UgTWFuYWdlbWVudDEVMBMGA1UEAwwMTUMgUm9v
            dCBDZXJ0MB4XDTE5MDUwMTA3MTQzMVoXDTI5MDQyODA3MTQzMVow
            fjELMAkGA1UEBhMCVVMxEzARBgNVBAgMCkNhbGlmb3JuaWExEjAQ
            BgNVBAcMCUN1cGVydGlubzETMBEGA1UECgwKQXBwbGUgSW5jLjEa
            MBgGA1UECwwRRGV2aWNlIE1hbmFnZW1lbnQxFTATBgNVBAMMDE1D
            IFJvb3QgQ2VydDCCAiIwDQYJKoZIhvcNAQEBBQADggIPADCCAgoC
            ggIBAJYUAHIa+Dr5CBsxD962SE75XntS3fLF2DbHtqScpuzlEXDx
            /2isUXuJVHXvSdZLwbjEDRJ11yZSoK1S12U8UTKUl+bGQ/Gn71VB
            gnV6aqbdVW4E8lImMk7jZDMH1mxkw19fGtDDhEN105Gx7+dUnJs1
            7s4p+jbHQ8po3Hck4nUz82U6JRbWuNRdSq5b/h3SW9A3iZ1tODyM
            lLN+VrhtDbLaE/TFY5xZ/v4bRfvEFJ6/UT6lg7EZ+r0XvycWKo2v
            T/fOuEGmNBs1rbcOgwiBVDR7WDnOotTVDm1LrtVEamVYcPwqJ9nc
            MaJMxcMI4vCk4xxPp7/cxBspd0+gbGYXIYdbr9bS6CTa0y3Nb1x+
            vrY7TSXPGHTMC0/apPCmBF0rDWs6mYs+E+4PhCKh52xTQ8zyZ5Q6
            Nr9XjQRJj9vbJkjL1656rpTPEWmBS2qCVjMLilP80a505dwI1c6p
            kSkP730kHhLmCTxfBpoRbwZy1kBMj3laZA9cmTRQbOZP2F35Unvl
            5/1n4nVwCxGS3se55lnw8wK5/FkAazmKWCw0NvcEG9OAmAB+5jZU
            WMewhzqrMgLP1PnmjGKpzctto/NlPdOuAXggP4f9OiY26UxSGqny
            GhWjiHm6Hyy/1cn5tXeSLqVHK6hirH6MhzK8+DyFH67Dwvb2NtJR
            HZuHSoAWTpKfAgMBAAEwDQYJKoZIhvcNAQELBQADggIBAGUixT10
            inJqUjoCmMjG6Rp/XFEHg6hBiz8U/yRVPHo0oQ4TDvr0X0E9y7/+
            waw9rZHE7jwUNzwmYvEyl036BpT2UVAioX0206jreWJOgMV1lYAU
            hXe65zivjOVDOkTQWiFJozcmv0uvZnk+EixxPrPBX98NXQ4AyUky
            KngY5GJyOmnb+vgRQB3nrMzImr2zLMbZvomCOZDWAJdawRSYMpE8
            fkyPfv7C5V9wKVYqTRMwQDnMX/X9yATMutAet15w7kZ7rXzw8dLc
            dPp2PRBBHzmdYawzflWVOgA+7GI70Vgm4DzRLBVbciG2eMfTKXzf
            Wxg+lxPilZs/6Of5hocuTVyXDxrgE0D6KlUR+i47z/d4Sik+IWIF
            LwcmW8HEzQ2W9SjApH4ShhD+0sQt6o6L604r0jO1mHXnHqJcFFeZ
            b9N72k0IMe2o0Z+iwubbXjfPg9LWQ3jeI9ROfBsZP5fA52LbFPyR
            bJLN89xrnCxKvO5lPzvXzpaykECVDmNkIY2TNXn2RufAWCazEUiK
            wiOCRKf2RLpOfTonHaWHf/A70jY2WoRFCyZWPgCu6Amd0SM+zvrm
            MB/R/6BaT/X1crAPGP+6EsSFxpdDrjeGKaiX3ytReAJqE0APakx8
            CWGhZ2EU9Igcyh516lf89yTq0DliBR3CYRenl0ba1+z3RzVVaEh/

            IsIdentity

            CommonName
            Device Certificate
            Data

            MIIEQjCCAiqgAwIBAgICAaIwDQYJKoZIhvcNAQELBQAwfjELMAkG
            A1UEBhMCVVMxEzARBgNVBAgMCkNhbGlmb3JuaWExEjAQBgNVBAcM
            CUN1cGVydGlubzETMBEGA1UECgwKQXBwbGUgSW5jLjEaMBgGA1UE
            CwwRRGV2aWNlIE1hbmFnZW1lbnQxFTATBgNVBAMMDE1DIFJvb3Qg
            Q2VydDAiGA8yMDE5MDkvNDA0MDgyN1oYDzIwMTkxMDA0MDQwODI3
            WjAyMRMwEQYDVQQKEwpBY21lLCBJbmMuMRswGQYDVQQDExJEZXZp
            Y2UgQ2VydGlmaWNhdGUwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAw
            ggEKAoIBAQDHZSEI6rkl/ELttn5zIb+0R5N7sXKgXwrQhWRNIMys
            xjql8LEDnPbIJnx0K2VrxjPrdAbHnirtwp9MmO//TUCtiHcIDtQT
            K5YE6HZHjEeQDuqRhcTtSfCG6dhpdrO284XD57L3j8aHY65d+vi4
            RUnxS7SrOHUj4/C4XIpy+upEmvMuGyHJxzJJceRa+rhYqYoi3qkG
            4cWfPZ5zHV4kQF4DVZsIWFXry0IhnHjFTMMrmIUctK/zAd4ldVwl
            f9Tt2y0g5F5nDatrVLKXce3avx21oVMh53Z7OlqQI7e2QhwmnMBP
            rsIgO4RPpxcAw2JnZqWj9yE6y2zS6Eho1zYDldWxAgMBAAGjEjAQ
            MA4GA1UdDwEB/wQEAwIFoDANBgkqhkiG9w0BAQsFAAOCAgEAauHB
            JMkRqyVpKMOmc1dH3iA69AHbGGJlTht0gAZk9SksIbOQ1E2pIBBd
            P8jBk+DMXTwXTcSpzHVw9cQroKj6U69U8w21y0d1S6Paw3xHp3HP
            bd/zjU+jBO2QbPmS3yorYPeHWAmU/JQ1WsawjKCVAaLjckK3fjqM
            fbdzq7oxON9wajsvx6aV+SGUfchvXYOV1aBLtMyDMeb397cRvHcD
            AxWJF55f3vCfwtNJ2ByaC9UhSDpaLOWVea87zP6WZBQ8B2jsdu8y
            sTSJdgAOjLYD0YD6DXBhxGixCGdaZpUPGsIQ8I1BNPmImKdnvxv2
            TaU1v6TqwOocbhngLszf3ZPXHAk/PGoLJGyHgov7qfoCkJFYLiEl
            CJNQzBDER60Pm8RukbKBbZ0oGW6+BiRK32x41ICWXZ3QcEo/eRu4
            QRQB5h65k/xVyez2Fwj8kDut/F7W0OBnNHuMnH/UEftbO2OxbVY6
            psF7eZO+4XyTH3TaYkUeZDDgU6rvPmvcyzk4MDP0LnN8vcwex+N2
            G6hyZDLsyW351R3dBmCkm2kLjwNAzJqf3JKOk2f7N7HTvUby7X0j
            JpOvmy4h56wW1vIYpt8LE/SBp7wldsLxiYsLBsbtBSh7w/7eAIU8
            lHsQh3MCk4mBRrrtedXGdwcmceXtXBJvvmogX8z+n3I4ItuE6IcU
            2sE=

            IsIdentity

    CommandUUID
    0001-CertificateList
    Status
    Acknowledged
    UDID
    00008020-000915083C80012E

```

## Topics

### Command and Response

object CertificateListCommand

The command to get a list of installed certificates on a device.

object CertificateListResponse

A response from the device after it processes the command to get a list of installed certificates.

## See Also

### Security

Security Information

Get security-related information about a device.

Get the Bypass Code for Activation Lock

Get the code to bypass Activation Lock on a device.

Clear the Bypass Code for Activation Lock

Clear the Activation Lock bypass code on a device.

Rotate the FileVault Key

Change the FileVault primary password on a device.

