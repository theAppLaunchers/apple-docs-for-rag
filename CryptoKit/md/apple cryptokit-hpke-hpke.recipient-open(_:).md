

- Apple CryptoKit
- HPKE
- HPKE.Recipient
-  open(\_:) 

Instance Method

# open(\_:)

Decrypts a message, if the ciphertext is valid.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

``` source
mutating func open(_ ciphertext: C) throws -> Data where C : DataProtocol
```

## Parameters 

`ciphertext`  

The ciphertext message to decrypt.

## Return Value

The resulting cleartext message if the message is authentic.

## Discussion

You can call this method multiple times to decrypt a series of messages. When using this method, the recipient of the ciphertext messages needs to decrypt them in the same order that the sender encrypts them.

Note

The system throws errors from HPKE.Errors when it encounters them.

