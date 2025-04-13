

- LightweightCodeRequirements
- ProcessCodeSigningFlags
- ProcessCodeSigningFlags.ValueSet
-  terminatesOnCodeSigningFailure 

Type Property

# terminatesOnCodeSigningFailure

Code signing failures on page in should cause the process to be terminated.

iOS 17.4+iPadOS 17.4+Mac Catalyst 17.4+macOS 14.4+tvOS 17.4+visionOS 1.1+watchOS 10.4+

``` source
static let terminatesOnCodeSigningFailure: ProcessCodeSigningFlags.ValueSet
```

## Discussion

This flag may be present on any on disk signature. This flag only has effect on main executables. This is equivalent to `CS_KILL` in C APIs.

