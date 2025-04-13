

- Authentication Services
- ASImportableCredential
- ASImportableCredential.TOTP
-  init(secret:period:digits:username:algorithm:issuer:) 

Initializer

# init(secret:period:digits:username:algorithm:issuer:)

Creates a time-based one-time password (TOTP) instance.

iOS 18.2+iPadOS 18.2+Mac Catalyst 18.2+macOS 15.2+visionOS 2.2+

``` source
init(
    secret: Data,
    period: UInt16,
    digits: UInt16,
    username: String,
    algorithm: ASImportableCredential.TOTP.Algorithm,
    issuer: String? = nil
)
```

## Parameters 

`secret`  

The secret associated with this generator.

`period`  

The period, in seconds, used by the generator to refresh codes.

`digits`  

The number of digits in the code used by the generator.

`username`  

The username associated with the generator.

`algorithm`  

The algorithm used by the generator.

`issuer`  

The issuer of the generator, if any.

