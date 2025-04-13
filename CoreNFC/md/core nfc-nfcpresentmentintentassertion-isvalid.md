

- Core NFC
- NFCPresentmentIntentAssertion
-  isValid 

Instance Property

# isValid

A Boolean property that indicates whether the presentment intent assertion instance is still valid.

iOS 17.4+iPadOS 17.4+

``` source
final var isValid: Bool { get }
```

## Discussion

This value is `true` when you first acquire a presentment intent assertion. It becomes `false` when any of the following occur:

- Your app goes into the background.

- The maximum presentment intention assertion duration expires.

## See Also

### Testing presentment intention validity

enum Error

An error type that indicates problems with the presentment intent assertion.

