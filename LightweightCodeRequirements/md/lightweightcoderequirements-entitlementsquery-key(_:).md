

- LightweightCodeRequirements
- EntitlementsQuery
-  key(\_:) 

Type Method

# key(\_:)

Match against the specified key name at the root of the entitlements dictionary.

iOS 17.4+iPadOS 17.4+Mac Catalyst 17.4+macOS 14.4+tvOS 17.4+visionOS 1.1+watchOS 10.4+

``` source
static func key(_ keyName: String) -> EntitlementsQuery
```

## Discussion

Keys are matched byte for byte (i.e. no unicode normalization occurs). Chain additional qualifiers to constrain the value of the key.

