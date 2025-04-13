

- LightweightCodeRequirements
- ProcessCodeSigningFlags
- ProcessCodeSigningFlags.ValueSet
-  isDynamicallyValid 

Type Property

# isDynamicallyValid

Flag indicating that no code signing validation errors have been found for the process.

iOS 17.4+iPadOS 17.4+Mac Catalyst 17.4+macOS 14.4+tvOS 17.4+visionOS 1.1+watchOS 10.4+

``` source
static let isDynamicallyValid: ProcessCodeSigningFlags.ValueSet
```

## Discussion

This is equivalent to `CS_VALID` in C APIs.

