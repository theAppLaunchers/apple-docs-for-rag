

- Authentication Services
- Platform single sign-on (SSO)
- Authentication process
-  Performing encryption verification 

Article

# Performing encryption verification

Verify the login request and create a JSON Web Encryption (JWE) response.

## Overview

Use the code snippets in this article to complete the process of encryption verification that works with platform SSO:

- Create device signing and encryption keys

- Sign the login request and encrypt the response

- Perform key exchange

- Derive a shared key and encrypt the plain text

- Verify the login response and decrypt the JWE

Use this device signing key:

```
{
    "y" : "PAIz7YrH4Rxz1rlfn6JcnwSmFDVGY1ISlGnmK1NX5vs",
    "d" : "vXZoCHYVxEJVcCcQN50ZKEBwhlQYO6g3KaUIufh3vXw",
    "kid" : "Ws9mKynZxyUSNXYtMGAjjLO+Jg16HCa\/5pJO0udNWJ4=",
    "x" : "gK60EgxT-EipyAgSlrHG0LgFVrgnd8UXAvLOgykJtms",
    "kty" : "EC",
    "crv" : "P-256"
}
```

Use this device encryption key:

```
{
    "y" : "4MlSuUf_7J6Ljv0FBT1jK0_sKGB4WYwdKCOtnTEAwz4",
    "d" : "1bqqmpoFEtzSnQMqp9N9ZRybnP8vjFUiZyGaSgKVGMw",
    "kid" : "pScnuzx3x85Eyp6CtK9UQADxOsAGTP72y02Tg3m1sk8=",
    "x" : "TvkPOH4yscrSC1rFYvnBVPYMqzR1vKck9ht4D7K_gAQ",
    "kty" : "EC",
    "crv" : "P-256"
}
```

### Sign the login request

Note how the system signs the following login JSON Web Token (JWT) using the device-signing key:

```
{
    "kid" : "Ws9mKynZxyUSNXYtMGAjjLO+Jg16HCa/5pJO0udNWJ4=",
    "x5c" : "MIIBhDCCASmgAwIBAgIBATAKBggqhkjOPQQDAjA3MRQwEgYDVQQDEwtkZXZpY2UgdGVzdDELMAkGA1UEBhMCVVMxEjAQBgNVBAoTCUFwcGxlIEluYzAeFw0yMjA2MjMxNzI1MzFaFw0yMzA2MjMxNzI1MzFaMDcxFDASBgNVBAMTC2RldmljZSB0ZXN0MQswCQYDVQQGEwJVUzESMBAGA1UEChMJQXBwbGUgSW5jMFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAEgK60EgxT+EipyAgSlrHG0LgFVrgnd8UXAvLOgykJtms8AjPtisfhHHPWuV+folyfBKYUNUZjUhKUaeYrU1fm+6MmMCQwEgYDVR0TAQH/BAgwBgEB/wIBADAOBgNVHQ8BAf8EBAMCB4AwCgYIKoZIzj0EAwIDSQAwRgIhAMwGOYwgf5xGxNcZLL/Y4phA66w/PSVLeQYhec2JTQF1AiEAlNSUDycvv0DwDQYU4wUpco/GBuhc4mPmli3+DT+p1Is=",
    "typ" : "JWT",
    "alg" : "ES256"
}.{
    "iat" : "1656005132",
    "jwe_crypto" : {
        "alg" : "ECDH-ES",
        "enc" : "A256GCM",
        "apv" : "AAAABUFwcGxlAAAAQQRO-Q84fjKxytILWsVi-cFU9gyrNHW8pyT2G3gPsr-ABODJUrlH_-yei479BQU9YytP7ChgeFmMHSgjrZ0xAMM-AAAAJERERjY4MTcxLTQwOUQtNEUyQy05MUYwLTlFNDJENzc0NTM2NQ"
    },
    "password" : "bar",
    "request_nonce" : "AwABAAAAAAADAOz_BADv_xtgu_SM1Mvoq02PYz_YfXxx5FAgcLHLNikH6gjrBWwcqnRW_haxqO9JCiPat5KfkTily04S8EH3AQwVsWCxHYQgAA",
    "scope" : "openid offline_access urn:apple:platformsso",
    "grant_type" : "password",
    "username" : "foo",
    "aud" : "https://localhost.apple.com:8888/auth/token",
    "client_id" : "aaff1524-fa35-40c5-94e3-2b233c5f2965",
    "nonce" : "DDF68171-409D-4E2C-91F0-9E42D7745365"
}
```

The signed and encoded login JWT output is:

```
```

### Encrypt the response

Use the following ephemeral key, response header, and plain text to generate a sample encrypted response. The plain text is encrypted and all data values are base-64 URL encoded.

Ephemeral key  
`{`

`“y” : “erf9nEkEC8SiuwP-7f7udD7CnX5KEauVIfBPoqnmlYo”,`

`“d” : “okDfU7IYlFXoEKgqu-79iy-AR55omCKzVKlFCXy8z5c”,`

`“kid” : “lssbzDeX5i7SjBnCsHVKrzAMnEvEmVwZeyJQqoGdS4E=”,`

`“x” : “VIXdgu3x0eLgEVtROZ5YQ4GUS8WZQT-3HPqX2FPoY4I”,`

`“kty” : “EC”,`

`“crv” : “P-256”`

`}`

Response header  
`ewogICJlbmMiIDogIkEyNTZHQ00iLAogICJraWQiIDogInBTY251engzeDg1RXlwNkN0SzlVUUFEeE9zQUdUUDcyeTAyVGczbTFzazg9IiwKICAiZXBrIiA6IHsKICAgICJ5IiA6ICJlcmY5bkVrRUM4U2l1d1AtN2Y3dWREN0NuWDVLRWF1VklmQlBvcW5tbFlvIiwKICAgICJ4IiA6ICJWSVhkZ3UzeDBlTGdFVnRST1o1WVE0R1VTOFdaUVQtM0hQcVgyRlBvWTRJIiwKICAgICJrdHkiIDogIkVDIiwKICAgICJjcnYiIDogIlAtMjU2IgogIH0sCiAgImFwdSIgOiAiQUFBQUJVRlFVRXhGQUFBQVFRUlVoZDJDN2ZIUjR1QVJXMUU1bmxoRGdaUkx4WmxCUDdjYy1wZllVLWhqZ25xM19aeEpCQXZFb3JzRF91My03blEtd3AxLVNoR3JsU0h3VDZLcDVwV0siLAogICJ0eXAiIDogIkpXVCIsCiAgImFsZyIgOiAiRUNESC1FUyIKfQ`

Plain text  
`ewogICJyZWZyZXNoX3Rva2VuIiA6ICJBd0FCQUFBQXZQTTFLYVBsckVxZEZTQnpqcWZUR0FNeFpHVVRkTTB0NEI0IiwKICAiaWRfdG9rZW4iIDogImV3b2dJQ0owZVhBaUlEb2dJa3BYVkNJc0NpQWdJbUZzWnlJZ09pQWlVbE15TlRZaUxBb2dJQ0pyYVdRaUlEb2dJblYwYzB0aGVsWklVSFk0VFhoRFIwOXhORmcxWW14VFp6RjFRVFpCYkhWV2NYaE5SVWxTTjB0bGVUZzlJZ3A5LmV3b2dJQ0p1YjI1alpTSWdPaUFpUkVSR05qZ3hOekV0TkRBNVJDMDBSVEpETFRreFJqQXRPVVUwTWtRM056UTFNelkxSWl3S0lDQWlhV0YwSWlBNklDSXhOalUyTURBMU1UTXlJaXdLSUNBaWJtSm1JaUE2SUNJeE5qVTJNREExTVRNeUlpd0tJQ0FpZFhCdUlpQTZJQ0ptYjI4aUxBb2dJQ0psZUhBaUlEb2dJakUyTlRZd01EVTBNeklpTEFvZ0lDSmhkV1FpSURvZ0ltRmhabVl4TlRJMExXWmhNelV0TkRCak5TMDVOR1V6TFRKaU1qTXpZelZtTWprMk5TSXNDaUFnSW1semN5SWdPaUFpYUhSMGNITTZMeTltYjI4dWFYTnpkV1Z5TG1OdmJTSUtmUS5HMi1EcWhBaUoxaTZPS3JYdjh2ZzVWcjhWWXFxcW1ZdnZ1U2FQSmZ3c0xEb3QyaXZIdzJhbGp5WG5na05WaDYtTmtrZXZHWnRJUnFTcE9yMGY5czB6XzlmazJmajJzb3lHOWlOMFJoSmNJLV9xSG9hTGxrZWFDNFF2WTZ4alZRMnVqOG5iUnBIRVN4VGRoSi1LSjZfMm1BVGk3NVZxUmlfV3NBMElLZnhCaGc4Y01aS25lMF9pTTRoRERqQVFQR2N2SWtMcG5nT1BTbWRHbUxNUkZVU0twVVBQYmt0QzRHa0Y0T1VBZXJFS0VORFdlZHhpU2pCa2VwOW1ZVV9MdDNFM2o0RU1ZVFVyTDNZeU1XTGotdnRUY2ttVTJCZHNvMHlfbnlfMDhpWWdPVXJ2OGJwdlkxQTdoc1NwZWM5ZTYwMWRKSHAxekx3NVppbzhjVVl0MnFKalEiLAogICJleHBpcmVzX29uIiA6ICIxNjU2MDMzOTMyIiwKICAidG9rZW5fdHlwZSIgOiAiQmVhcmVyIiwKICAiZXhwaXJlc19pbiIgOiAyODgwMCwKICAicmVmcmVzaF90b2tlbl9leHBpcmVzX2luIiA6IDI4ODAwCn0`

### Perform Diffie-Hellman key exchange

Diffie–Hellman key exchange is a method to securely exchange cryptographic keys over a public channel.

Use the device encryption public key and the ephemeral private key to perform Diffie-Hellman key exchange (ecdhKeyExchangeStandard).

Exchanged key (output)  
`L87ywmD3aLpVlXsqAvq7udyr4s6M0y9MjQCytE71epA`

### Perform ConcatKDF

ConcatKDF is a concatenation Key Derivation Function (KDF) to derive a shared key from the result of performing Diffie-Hellman key exchange.

Perform ConcatKDF using the key exchange result, algorithm, `PartyUInfo`, and `PartyVInfo`: Here are the values that these code snippets use, including the data before the hash and the computed key (output):

`Z` (The result of the Diffie-Hellman key exchange)  
`L87ywmD3aLpVlXsqAvq7udyr4s6M0y9MjQCytE71epA`

Algorithm  
`QTI1NkdDTQ`

`PartyUInfo`  
`AAAABUFQUExFAAAAQQRUhd2C7fHR4uARW1E5nlhDgZRLxZlBP7cc-pfYU-hjgnq3_ZxJBAvEorsD_u3-7nQ-wp1-ShGrlSHwT6Kp5pWK`

`PartyVInfo`  
`AAAABUFwcGxlAAAAQQRO-Q84fjKxytILWsVi-cFU9gyrNHW8pyT2G3gPsr-ABODJUrlH_-yei479BQU9YytP7ChgeFmMHSgjrZ0xAMM-AAAAJERERjY4MTcxLTQwOUQtNEUyQy05MUYwLTlFNDJENzc0NTM2NQ`

ConcatKDF data before SHA-256 hash  
`AAAAAS_O8sJg92i6VZV7KgL6u7ncq-LOjNMvTI0AsrRO9XqQAAAAB0EyNTZHQ00AAABOAAAABUFQUExFAAAAQQRUhd2C7fHR4uARW1E5nlhDgZRLxZlBP7cc-pfYU-hjgnq3_ZxJBAvEorsD_u3-7nQ-wp1-ShGrlSHwT6Kp5pWKAAAAdgAAAAVBcHBsZQAAAEEETvkPOH4yscrSC1rFYvnBVPYMqzR1vKck9ht4D7K_gATgyVK5R__snouO_QUFPWMrT-woYHhZjB0oI62dMQDDPgAAACREREY2ODE3MS00MDlELTRFMkMtOTFGMC05RTQyRDc3NDUzNjUAAAEA`

Computed key (output)  
`kh36uWSGH25r09lLf3m5l3TLS5xKAs-h3UCdbTKheCY`

### Encrypt the plain text

The system uses the key from ConcatKDF with the Initialization Vector (IV) and the Additional Authentication Data (AAD) to encrypt the plain text using AESGCM. The AAD is the ASCII-encoded response header per RFC 7516 Section 5.1, Step 14. The response header was already base-64 URL encoded. Here are the values that these code snippets use, and the output:

Key (from ConcatKDF)  
`kh36uWSGH25r09lLf3m5l3TLS5xKAs-h3UCdbTKheCY`

IV  
`cFAKroCUiODyXmdK`

AAD  
`ZXdvZ0lDSmxibU1pSURvZ0lrRXlOVFpIUTAwaUxBb2dJQ0pyYVdRaUlEb2dJbkJUWTI1MWVuZ3plRGcxUlhsd05rTjBTemxWVVVGRWVFOXpRVWRVVURjeWVUQXlWR2N6YlRGemF6ZzlJaXdLSUNBaVpYQnJJaUE2SUhzS0lDQWdJQ0o1SWlBNklDSmxjbVk1YmtWclJVTTRVMmwxZDFBdE4yWTNkV1JFTjBOdVdEVkxSV0YxVmtsbVFsQnZjVzV0YkZsdklpd0tJQ0FnSUNKNElpQTZJQ0pXU1Zoa1ozVXplREJsVEdkRlZuUlNUMW8xV1ZFMFIxVlRPRmRhVVZRdE0waFFjVmd5UmxCdldUUkpJaXdLSUNBZ0lDSnJkSGtpSURvZ0lrVkRJaXdLSUNBZ0lDSmpjbllpSURvZ0lsQXRNalUySWdvZ0lIMHNDaUFnSW1Gd2RTSWdPaUFpUVVGQlFVSlZSbEZWUlhoR1FVRkJRVkZSVWxWb1pESkROMlpJVWpSMVFWSlhNVVUxYm14b1JHZGFVa3g0V214Q1VEZGpZeTF3WmxsVkxXaHFaMjV4TTE5YWVFcENRWFpGYjNKelJGOTFNeTAzYmxFdGQzQXhMVk5vUjNKc1UwaDNWRFpMY0RWd1Ywc2lMQW9nSUNKMGVYQWlJRG9nSWtwWFZDSXNDaUFnSW1Gc1p5SWdPaUFpUlVORVNDMUZVeUlLZlE`

Cipher text (output)  
`MHlVmPIlP5Tz9pKKMLJfHTKkWtHpP1Y8YKAdT7iuRN09bTNRgArfPLIlo7WkUolOGoU3oV07p3m3cOmTzmVqOmVs0dXlEVZlF21TX_hjN2sj5RpC4tWBdKVdoCej4u0Brkgypw0jXtKUzjIM2HcE-8Yy4fC-ixTnescR1M3eM_6IWRR1MtEYTy1C7JrBcw9gZVSmvC1DpeH49gYw9FkIQUpdnfvyreVU0DfvqhABvp29fpVmQqoaENoLuqDt0Ajfko5LWRz3sLcZipoZ0gdRgwQpcNLnBUYAZs5D7t8Yuay2CZjAoTZcbFv4F8Mrg2BgEncVwhC9jTEVGe3GinlsziPdSVIt-7lXbV99yk2qX0eYb4ItScWgUfl3y_p623Xtr3AOxlslahF7fm8PN3sAJnwb_aQQxeeQZQyRZKD9uMHHUTMZeoJbXxV1KdGgQMYdW0Z40_WYFtqT8UwboptazbZX02GOmz2gO7JSe0OHgLCPAfvp9Ah2apYrEDqp01tYwhCG8SNuBB_sXPuJx-euUuxu70s1809k44A_hAc_iYDPwTBpAXBLOiuJIxVZgy54WNNiP_WqBImjsA1ioE7Mrvqkn-DnkM0NP2rt1GvaZ-IpUNgAXKudjiT51guQLnRcr9r3pNmmIaUrqKepMJdAYqUbc9PjYUus7RX-20r5pudVi8Ef0Tg5y9Hk3f7sfiX9peBea_L5yQP-tjXJN8lITRBFCtvvsTb0ALVbKTTHiItmYFxl7XzAljiOMiXEKDKwb0VqOtkU4Ljdz2_M7mW0sT1M6_8XZ6dn3W9RMAeqmLnKlxU5gxj0rK5C8Dnok-I2jOlDzr7uS01WBmaln4E2MTRLyGsdUhXk6JLewtomMTrM7dfq1x6iZubbV8fOk4ayKlEh6xQONPfUXAnr-OB45gllZ2GWNaipd9nwJyGnktSQYpjHiMgl-eKQ3nwwD6Tnj9yYZgvq-D5_DUknvk1XMGTF1CAKaGWDWvf4t2LTyxLld6qgDKyrQWYVKRbHY5LtUqlQjTUP9WGVCNnojVfEIVJIxGXspgL_QwViuBBkmHa_IEd18UE68_yhtBh1dxi_K3td6AG01_Fm1UgYNhi4SPHJqA22zJQ397HdAAGk1bYk5IacY9qyqpVXPBRhEE92DG5oDZcCUB9li87NWRJIaF46Q1z5S2ROSBimBi-nyOX5G4DpgrPjst3lK7NacpssjdPk2fDh3XXKu2r4RXBr7l7hweuwKNgyzPBoTZ37dadYKz1MpxO5Ag43xLzTougLDkVrS5w`

Tag (output)  
`4dpX5cVdPodXep2NyC2Vyg`

### Verify the login JWE response

Check the response to confirm that it matches the following output when formatted as a JWE with compact serialization. The system formats the response per RFC 7516 Section 5.1, Step 19. The JWE encrypted key is empty because the system uses direct key agreement:

```
```

### Decrypt the JWE

The system calculates the key differently when decrypting the JWE. For decryption, the system performs Diffie-Hellman key exchange (ecdhKeyExchangeStandard) using the device encryption private key and the ephemeral public key from the JWE header. The other inputs for ConcatKDF are the same and the system uses the calculated key for AESGCM decryption using the fields from the encrypted JWE.

## See Also

### Login response

Creating a JSON Web Encryption (JWE) login response

Create an encrypted login response and configure the concatenation key derivation function (Concat KDF).

Processing the JSON Web Encryption (JWE) login response

Validate the encrypted response.

