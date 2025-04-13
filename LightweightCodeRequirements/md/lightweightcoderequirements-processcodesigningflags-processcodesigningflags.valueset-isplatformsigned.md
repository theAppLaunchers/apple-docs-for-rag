

- LightweightCodeRequirements
- ProcessCodeSigningFlags
- ProcessCodeSigningFlags.ValueSet
-  isPlatformSigned 

Type Property

# isPlatformSigned

Flag indicating that the binary has been identified as a platform binary (Apple Signed).

iOS 17.4+iPadOS 17.4+Mac Catalyst 17.4+macOS 14.4+tvOS 17.4+visionOS 1.1+watchOS 10.4+

``` source
static let isPlatformSigned: ProcessCodeSigningFlags.ValueSet
```

## Discussion

This is equivalent to `CS_PLATFORM_BINARY` in C APIs.

